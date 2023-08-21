Energy Efficiency - Example
============================

Simple Example
----------------

Let's revisit the vector dot product.
While this is not the most inspiring example, it has the advantage of being comprehensible by most with algebra/calculus background and illustrates how the coding can *quickly* become more complicated than the mathematics itself.

In this simple case study, we are going to examine how to improve energy efficiency of this basic algorithm by making use of OpenMP (for basic parallelism) and SIMD instructions on ARM64. 

This is not a complete write-up yet.

Does OpenMP know how to work energy-efficient procesors such as ARM with SIMD instructions?
-----------------------------------------------------------------------------------------------

OpenMP can work efficiently with energy-efficient processors such as ARM. OpenMP is a portable programming model that supports shared memory parallel programming in C, C++, and Fortran on all platforms, including ARM.

Specifically, OpenMP 4.0 and later versions introduce directives for vectorization, which can take advantage of SIMD (Single Instruction, Multiple Data) instructions available on modern processors. SIMD instructions perform the same operation on multiple data points simultaneously, which can significantly improve computational efficiency.

For ARM processors, the ARM NEON technology is a SIMD architecture extension, providing a wide range of SIMD instructions that can be used to improve the performance of many types of applications, including signal processing and multimedia applications.

Therefore, to write efficient OpenMP code for ARM processors, you'll need to be familiar with how to best utilize OpenMP directives for vectorization in combination with ARM's SIMD capabilities. It's also beneficial to understand the specific characteristics of your ARM processor, such as its memory hierarchy and core configuration, as these can also impact performance.

It's worth noting that simply using OpenMP or SIMD instructions doesn't automatically guarantee optimal performance. It requires careful programming and performance tuning to fully exploit the capabilities of your hardware. OpenMP is just a tool, and like all tools, it needs to be used properly to get the best results.

Lastly, keep in mind that using energy-efficient processors like ARM is one way to improve the energy efficiency of your computation, but there are many other factors to consider as well, including the algorithms you use, the memory access patterns of your code, and the overall system configuration.


Simple Dot Product
--------------------


.. code-block:: c

   #include <stdio.h>
   #include <stdlib.h>
   
   double dot_product(double* a, double* b, int size) {
       double result = 0.0;
       for(int i = 0; i < size; i++) {
           result += a[i] * b[i];
       }
       return result;
   }
   
   int main(int argc, char* argv[]) {
       if(argc != 2) {
           printf("Usage: %s <size>\n", argv[0]);
           return 1;
       }
   
       int size = atoi(argv[1]);
   
       double* a = (double*)malloc(size * sizeof(double));
       double* b = (double*)malloc(size * sizeof(double));
   
       // Initialize vectors
       for(int i = 0; i < size; i++) {
           a[i] = (double)i;
           b[i] = (double)(size - i);
       }
   
       double result = dot_product(a, b, size);
   
       printf("Dot Product: %.2f\n", result);
   
       free(a);
       free(b);
   
       return 0;
   }



OpenMP Version
-----------------

You can easily parallelize the dot product computation using OpenMP. Here's how you could modify the `dot_product` function:

.. code-block:: c

    #include <omp.h>

    double dot_product(double* a, double* b, int size) {
        double result = 0.0;
        #pragma omp parallel for reduction(+:result)
        for(int i = 0; i < size; i++) {
            result += a[i] * b[i];
        }
        return result;
    }

Here's what we've done:

1. Added the `#include <omp.h>` preprocessor directive at the top of the program. This includes the OpenMP header file, which provides the functionality for parallel computing.

2. Added the `#pragma omp parallel for reduction(+:result)` directive before the loop. This directive tells the compiler to create a team of threads and distribute iterations of the loop among them. The `reduction(+:result)` clause ensures that each thread maintains its own private copy of the `result` variable, and at the end of the parallel region, all these private copies are added together in a thread-safe manner.

To compile this program with OpenMP support, you'll need to use an OpenMP-compatible compiler such as GCC, and you'll need to enable OpenMP support at compile time. Here's an example of how to do this using GCC:

.. code-block:: shell

    gcc -fopenmp dot_product.c -o dot_product

The `-fopenmp` option tells GCC to enable OpenMP support. The `-o dot_product` option tells GCC to output the compiled program to a file named `dot_product`.

Then, you can run the program as you would normally:

.. code-block:: shell

    ./dot_product

Please note, this OpenMP version of the code will work on any CPU that supports OpenMP, not just ARM CPUs. Also, the actual performance improvement will depend on the number of cores available on your CPU.

   
Using ARM64 Neon SIMD without OpenMP
---------------------------------------

In the following, we asked ChatGPT to show how to write a solution that not only uses OpenMP but also makes use of the superscalar (SIMD) mode on an ARM64 processor (found on Raspberry Pi and Apple M1/M2/M3 family).

.. note:: Much of this is still in flux. We don't exactly have all tooling neded to make this an out-of-box experience for most users. Even on Apple, LLVM suppport is still emerging. But that is the alluring aspect of this: Although not entirely ready for prime time, a nearly two-year-old snapshot of the internet helps Chat-GPT4 to give promising insight(s).


.. code-block:: c

    #include <stdio.h>
    #include <stdlib.h>
    #include <arm_neon.h>
    
    double dot_product(float* a, float* b, int size) {
        float32x4_t a_vec, b_vec, result_vec = vdupq_n_f32(0.0f);
        float result_array[4];
        double result = 0.0;
    
        for(int i = 0; i < size; i += 4) {
            a_vec = vld1q_f32(a + i);
            b_vec = vld1q_f32(b + i);
            result_vec = vmlaq_f32(result_vec, a_vec, b_vec);
        }
    
        vst1q_f32(result_array, result_vec);
        for(int i = 0; i < 4; i++) {
            result += result_array[i];
        }
    
        return result;
    }
    
    int main(int argc, char* argv[]) {
        if(argc != 2) {
            printf("Usage: %s <size>\n", argv[0]);
            return 1;
        }
    
        int size = atoi(argv[1]);
        // Ensure size is a multiple of 4
        size = (size + 3) / 4 * 4;
    
        float* a = (float*)malloc(size * sizeof(float));
        float* b = (float*)malloc(size * sizeof(float));
    
        // Initialize vectors
        for(int i = 0; i < size; i++) {
            a[i] = (float)i;
            b[i] = (float)(size - i);
        }
    
        double result = dot_product(a, b, size);
    
        printf("Dot Product: %.2f\n", result);
    
        free(a);
        free(b);
    
        return 0;
    }
    
       
What does the Neon float32x4_t do?
-------------------------------------

Here's a minimal example demonstrating how to use float32x4_t from the ARM Neon library to perform some basic SIMD operations. In this example, we perform element-wise addition, subtraction, multiplication and division on two 4-element float vectors:

.. code-block:: c

   #include <stdio.h>
   #include <arm_neon.h>
   
   int main() {
       // Initialize two 4-element float vectors
       float32x4_t a = {1.0f, 2.0f, 3.0f, 4.0f};
       float32x4_t b = {5.0f, 6.0f, 7.0f, 8.0f};
   
       // Perform element-wise addition
       float32x4_t result_add = vaddq_f32(a, b);
   
       // Perform element-wise subtraction
       float32x4_t result_sub = vsubq_f32(a, b);
   
       // Perform element-wise multiplication
       float32x4_t result_mul = vmulq_f32(a, b);
   
       // Perform element-wise division
       float32x4_t result_div = vdivq_f32(a, b);
   
       // Print results
       for(int i = 0; i < 4; i++) {
           printf("Element %d: Add = %.2f, Sub = %.2f, Mul = %.2f, Div = %.2f\n",
               i, result_add[i], result_sub[i], result_mul[i], result_div[i]);
       }
   
       return 0;
   }
   
Please note that SIMD operations operate on all elements of the vectors at once, which is what gives them their parallel processing capability. Also note that ARM Neon supports a wide range of SIMD operations beyond the ones shown in this example.

To compile this program on an ARM system, you would typically use a command like:

::

   gcc -O3 -march=armv8-a+simd program.c -o program

Can we use OpenMP and ARM64 Neon Together?
---------------------------------------------

Yes, OpenMP can still be used in conjunction with ARM's NEON SIMD instructions to further parallelize and optimize your code. 

Here is an example of how the `dot_product` function can be modified to use both OpenMP and NEON intrinsics:

.. code-block:: c

    #include <arm_neon.h>
    #include <omp.h>

    double dot_product(float* a, float* b, int size) {
        float result_array[4];
        double result = 0.0;

        #pragma omp parallel
        {
            float32x4_t a_vec, b_vec, result_vec = vdupq_n_f32(0.0f);

            #pragma omp for
            for(int i = 0; i < size; i += 4) {
                a_vec = vld1q_f32(a + i);
                b_vec = vld1q_f32(b + i);
                result_vec = vmlaq_f32(result_vec, a_vec, b_vec);
            }

            vst1q_f32(result_array, result_vec);

            #pragma omp atomic
            for(int i = 0; i < 4; i++) {
                result += result_array[i];
            }
        }

        return result;
    }

This version of the function divides the loop among multiple threads using OpenMP, with each thread calculating a partial dot product using NEON SIMD instructions. Each thread has its own `result_vec` variable, which is used to accumulate the dot product in SIMD fashion.

Then, after the loop, the partial results are added to the final `result` using the `atomic` directive, which ensures that the updates to the shared `result` variable are performed atomically, preventing race conditions.

This code assumes that the `size` is a multiple of 4, as each iteration of the loop processes four elements at a time. If this is not the case, you will need to handle the remaining elements separately.

Remember to compile with `-fopenmp` and `-mfpu=neon` flags when using GCC:

.. code-block::bash

   gcc -fopenmp -mfpu=neon dot_product.c -o dot_product

Also, as before, it's important to measure the performance of your code before and after these optimizations to ensure that they're actually improving performance. Depending on various factors such as the size of your data and the specifics of your hardware, it's possible that these optimizations could make your code slower, rather than faster.

Can we write the ARM64 Neon and OMP example to support Intel's SIMD?
----------------------------------------------------------------------

If you want to write an OpenMP parallelized code for the dot product that leverages Intel's SIMD instructions, you can use the Intel intrinsics for the SIMD operations and OpenMP for parallelizing the loop. Below is a simple example that utilizes OpenMP for parallelism and AVX2 for SIMD (256-bit wide vector operations).

.. code-block:: c

   #include <stdio.h>
   #include <stdlib.h>
   #include <immintrin.h>
   #include <omp.h>
   
   float dot_product(int n, float *a, float *b) {
       float result = 0.0f;
       __m256 sum = _mm256_setzero_ps();
   
       #pragma omp parallel for reduction(+:result)
       for(int i = 0; i <= n - 8; i += 8) {
           __m256 va = _mm256_loadu_ps(&a[i]);
           __m256 vb = _mm256_loadu_ps(&b[i]);
           __m256 prod = _mm256_mul_ps(va, vb);
           sum = _mm256_add_ps(sum, prod);
       }
   
       float temp[8];
       _mm256_storeu_ps(temp, sum);
       for(int i = 0; i < 8; i++) {
           result += temp[i];
       }
   
       // Handle the tail of the vectors, if the size is not a multiple of 8
       for(int i = n - (n % 8); i < n; i++) {
           result += a[i] * b[i];
       }
   
       return result;
   }

   int main(int argc, char *argv[]) {
       int n = 1000000; // Default vector size
       if (argc > 1) {
           n = atoi(argv[1]);
       }
   
       float *a = (float *)malloc(n * sizeof(float));
       float *b = (float *)malloc(n * sizeof(float));
       for(int i = 0; i < n; i++) {
           a[i] = 1.0f;
           b[i] = 1.0f;
       }
   
       float result = dot_product(n, a, b);
       printf("Dot product: %f\n", result);
   
       free(a);
       free(b);
       return 0;
   }


Here, we used OpenMP to parallelize the loop over the vectors and the AVX2 intrinsics to perform the SIMD multiplication and addition of the vectors. The AVX2 intrinsics use 256-bit wide vectors, allowing eight single-precision floating-point numbers to be processed at once.

You'll need to have a compatible compiler (like recent versions of GCC or Clang) and a processor that supports AVX2 to compile and run this code. A typical compile command might look like this:

::

   gcc -O3 -march=native -fopenmp program.c -o program

Make sure to replace "program.c" and "program" with the actual source and output filenames. The ``-march=native`` option tells the compiler to generate code that is optimized for the host CPU, and ``-fopenmp`` enables OpenMP support.

Please note that vectorization, especially manual vectorization, can be a complex subject, and the code may need to be carefully tuned to get the best performance on a specific processor or system.

Can we write a single version that can support both ARM64 and Intel/AMD?
--------------------------------------------------------------------------

.. note:: My original question asked about whether we could use something like the *strategy* design pattern to manage these in a single code base. GPT4 got there after a bit of prodding!

You can create a shared codebase that handles both ARM64 and x86_64 architectures by using preprocessor directives. Here's a simple example of how you can accomplish this:

.. code-block:: c

   #include <stdio.h>
   #include <stdlib.h>
   #include <omp.h>
   
   #ifdef __ARM_NEON
   #include <arm_neon.h>
   #endif
   
   #ifdef __AVX2__
   #include <immintrin.h>
   #endif

   float dot_product(int n, float *a, float *b) {
       float result = 0.0f;
   
   #ifdef __ARM_NEON
       float32x4_t sum = vdupq_n_f32(0.0f);
   #elif defined(__AVX2__)
       __m256 sum = _mm256_setzero_ps();
   #endif
   
       #pragma omp parallel for reduction(+:result)
       for(int i = 0; i <= n - 4; i += 4) {
   #ifdef __ARM_NEON
           float32x4_t va = vld1q_f32(&a[i]);
           float32x4_t vb = vld1q_f32(&b[i]);
           sum = vmlaq_f32(sum, va, vb);
   #elif defined(__AVX2__)
           __m256 va = _mm256_loadu_ps(&a[i]);
           __m256 vb = _mm256_loadu_ps(&b[i]);
           __m256 prod = _mm256_mul_ps(va, vb);
           sum = _mm256_add_ps(sum, prod);
   #endif
       }
   
   #ifdef __ARM_NEON
       float temp[4];
       vst1q_f32(temp, sum);
   #elif defined(__AVX2__)
       float temp[8];
       _mm256_storeu_ps(temp, sum);
   #endif
   
       for(int i = 0; i < 4; i++) {
           result += temp[i];
       }
   
       // Handle the tail of the vectors, if the size is not a multiple of 4
       for(int i = n - (n % 4); i < n; i++) {
           result += a[i] * b[i];
       }
   
       return result;
   }
   
   int main(int argc, char *argv[]) {
       int n = 1000000; // Default vector size
       if (argc > 1) {
           n = atoi(argv[1]);
       }
   
       float *a = (float *)malloc(n * sizeof(float));
       float *b = (float *)malloc(n * sizeof(float));
       for(int i = 0; i < n; i++) {
           a[i] = 1.0f;
           b[i] = 1.0f;
       }
   
       float result = dot_product(n, a, b);
       printf("Dot product: %f\n", result);
   
       free(a);
       free(b);
       return 0;
   }
   

The code uses preprocessor directives to determine whether it should use ARM64's NEON or Intel's AVX2 intrinsics. The shared parts of the code remain the same, and only the platform-specific parts are wrapped in conditional compilation blocks.

To compile this code, you'll need to use the appropriate compiler flags for the target architecture:

::

    gcc -O3 -march=native -fopenmp program.c -o program

For x86_64 with AVX2 support:

::

    gcc -O3 -march=native -fopenmp -mavx2 program.c -o program

The ``-march=native`` flag should allow the compiler to automatically detect and enable support for the appropriate SIMD instruction set based on the host CPU. If you need to target a specific CPU, you might replace ``-march=native`` with an appropriate ``-march``` option for that CPU.

Remember, this code assumes that the size of your vectors (:math:`n`) is a multiple of 4; otherwise, there will be some remaining elements that aren't handled by the SIMD code. The example handles these "tail" elements with a simple scalar loop after the main SIMD loop.

.. note:: This version has *most* of what I want, but I was not entirely happy that it used a least-common-denominator approach by using 4-wide SIMD. The AMD/Intel SIMD are 8-wide. This led me to the next version!

Improved version that uses the actual width of the CPU-specific SIMD mode
---------------------------------------------------------------------------

.. note:: This was driven by my interest in design patterns, e.g. strategy. My next stop is to show that we can do this without conditional compilation!

The following code uses 8-wide SIMD for the Intel version (using AVX2) and 4-wide SIMD for the ARM64 version (using NEON). This way, the code takes full advantage of the respective SIMD capabilities for each architecture.

.. code-block:: c

   #include <stdio.h>
   #include <stdlib.h>
   #include <omp.h>
   
   #ifdef __ARM_NEON
   #include <arm_neon.h>
   #endif
   
   #ifdef __AVX2__
   #include <immintrin.h>
   #endif
   
   float dot_product(int n, float *a, float *b) {
       float result = 0.0f;
   
   #ifdef __ARM_NEON
       float32x4_t sum = vdupq_n_f32(0.0f);
       int step = 4;
   #elif defined(__AVX2__)
       __m256 sum = _mm256_setzero_ps();
       int step = 8;
   #endif
   
       #pragma omp parallel for reduction(+:result)
       for(int i = 0; i <= n - step; i += step) {
   #ifdef __ARM_NEON
           float32x4_t va = vld1q_f32(&a[i]);
           float32x4_t vb = vld1q_f32(&b[i]);
           sum = vmlaq_f32(sum, va, vb);
   #elif defined(__AVX2__)
           __m256 va = _mm256_loadu_ps(&a[i]);
           __m256 vb = _mm256_loadu_ps(&b[i]);
           __m256 prod = _mm256_mul_ps(va, vb);
           sum = _mm256_add_ps(sum, prod);
   #endif
       }
   
   #ifdef __ARM_NEON
       float temp[4];
       vst1q_f32(temp, sum);
   #elif defined(__AVX2__)
       float temp[8];
       _mm256_storeu_ps(temp, sum);
   #endif
   
       for(int i = 0; i < step; i++) {
           result += temp[i];
       }
   
       // Handle the tail of the vectors, if the size is not a multiple of step
       for(int i = n - (n % step); i < n; i++) {
           result += a[i] * b[i];
       }
   
       return result;
   }
   
   int main(int argc, char *argv[]) {
       int n = 1000000; // Default vector size
       if (argc > 1) {
           n = atoi(argv[1]);
       }
   
       float *a = (float *)malloc(n * sizeof(float));
       float *b = (float *)malloc(n * sizeof(float));
       for(int i = 0; i < n; i++) {
           a[i] = 1.0f;
           b[i] = 1.0f;
       }
   
       float result = dot_product(n, a, b);
       printf("Dot product: %f\n", result);
   
       free(a);
       free(b);
       return 0;
   }
   
   
