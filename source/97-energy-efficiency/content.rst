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


Let's start with regular C program that does a dot product on two large vectors of floating point numbers.
-----------------------------------------------------------------------------------------------------------

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

OpenMP Version (no tricks)
-----------------------------

This is the OpenMP version.
Note that the parallelization happens in the `dot_product()` function. 
OpenMP parallelizes the outer loop.
It also uses the *reduction* operation to ensure that the final result is added together in the most efficient manner possible (on the target arch).


.. code-block:: c

   #include <stdio.h>
   #include <stdlib.h>
   #include <omp.h>
   
   double dot_product(double* a, double* b, int size) {
       double result = 0.0;
       #pragma omp parallel for reduction(+:result)
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
   
OpenMP + ARM64 Neon SIMD (no OpenMP)
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
    
       
