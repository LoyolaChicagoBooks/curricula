Performance/Benchmarking
=============================

.. note:: This section is inspired by my discusions with Isaac Ahlgren, who is working with me and Neil Klingensmith on research in context-based authentication and secure containerization. More to come!

Motivation
----------------------------------------------------------

Understanding theoretical running time is greatly emphasized in CS curricula.
This is vitally important but can be greatly improved by measuring *actual* performance (empirical/experimental analysis), which is a longstanding tradition in subdisciplines, e.g. high-performance and distributed computing systems.
This section aims to help students understand the state-of-the-art for measuring CPU, I/O, and Networking (a form of I/O) performance.


Tools
--------

The following benchmarks are common for analyzing CPU, I/O, and Network performnance.

.. csv-table::
   :header: "Title", "Description", "URL"
   :widths: 20, 50, 30

   "Cinebench", "Based on the Cinema 4D software, it tests the performance of CPUs at rendering 3D scenes.", "https://www.maxon.net/en/cinebench"
   "Geekbench", "A cross-platform benchmark that measures the CPU and memory subsystem performance through different workloads.", "https://www.geekbench.com/"
   "Prime95", "Although mainly used for stress testing CPUs (especially for overclockers), it's also used for CPU benchmarking.", "https://www.mersenne.org/download/"
   "SPEC CPU", "The Standard Performance Evaluation Corporation (SPEC) CPU benchmark is a well-respected benchmark for comparing high-performance CPUs in various applications.", "https://www.spec.org/cpu2017/"
   "Linpack / Intel Linpack", "Linpack is a software library for performing numerical linear algebra on digital computers. The Intel-optimized version is often used for benchmarking high-performance computing systems.", "https://software.intel.com/content/www/us/en/develop/articles/intel-math-kernel-library-linpack-download.html"
   "Iometer", "This is an I/O subsystem measurement and characterization tool for single and clustered systems.", "http://www.iometer.org/"
   "CrystalDiskMark", "A disk benchmark software that analyzes the drive's read and write speeds across multiple data block sizes.", "https://crystalmark.info/en/software/crystaldiskmark/"
   "ATTO Disk Benchmark", "ATTO Disk Benchmark measures storage systems' performance with various transfer sizes and test lengths for reads and writes.", "https://www.atto.com/disk-benchmark/"
   "fio", "It is a versatile I/O workload generator that can be used both for benchmarking and for verifying storage subsystems.", "https://fio.readthedocs.io/en/latest/fio_doc.html"
   "HD Tune", "HD Tune is a hard disk / SSD utility that includes various functions like measuring the drive's performance, scanning for errors, checking the health status.", "http://www.hdtune.com/"
   "iPerf / iPerf3", "iPerf is a widely used network testing tool that can create TCP and UDP data streams and measure the throughput of a network that is carrying them.", "https://iperf.fr/"
   "Netperf", "Netperf is another benchmark that can be used to measure the performance of different types of networking.", "https://www.netperf.org/netperf/"
   "Ping and Traceroute", "While they are not benchmarks in the traditional sense, ping and traceroute are often used in network diagnostics to measure round-trip time for packets and to trace the route packets take to reach a destination.", "Built into most operating systems"


CPU Benchmarking 
------------------

Top CPU-Only Benchmarking Tools

1. **Cinebench**: Based on the Cinema 4D software, it tests the performance of CPUs at rendering 3D scenes.
2. **Geekbench**: A cross-platform benchmark that measures the CPU and memory subsystem performance through different workloads.
3. **Prime95**: Although mainly used for stress testing CPUs (especially for overclockers), it's also used for CPU benchmarking.
4. **SPEC CPU**: The Standard Performance Evaluation Corporation (SPEC) CPU benchmark is a well-respected benchmark for comparing high-performance CPUs in various applications, often used in professional and scientific computing contexts.
5. **Linpack / Intel Linpack**: Linpack is a software library for performing numerical linear algebra on digital computers. The Intel-optimized version is often used for benchmarking high-performance computing systems, focusing on CPU and memory performance.


I/O Benchmarking
-------------------

Top I/O Benchmarking Tools

1. **Iometer**: This is an I/O subsystem measurement and characterization tool for single and clustered systems. It's widely used by storage vendors and industry analysts to benchmark network and local storage.
2. **CrystalDiskMark**: It is a disk benchmark software that analyzes the drive's read and write speeds across multiple data block sizes.
3. **ATTO Disk Benchmark**: ATTO Disk Benchmark measures storage systems' performance with various transfer sizes and test lengths for reads and writes.
4. **fio (Flexible I/O Tester)**: It is a versatile I/O workload generator that can be used both for benchmarking and for verifying storage subsystems.
5. **HD Tune**: HD Tune is a hard disk / SSD utility that includes various functions like measuring the drive's performance, scanning for errors, checking the health status, and securely erasing all data.


Network Benchmarking
-----------------------

Top Network Performance Benchmarking Tools

1. **iPerf / iPerf3**: iPerf is a widely used network testing tool that can create TCP and UDP data streams and measure the throughput of a network that is carrying them. It's very effective for testing bandwidth and quality of a network link.
2. **Netperf**: Netperf is another benchmark that can be used to measure the performance of different types of networking. It provides a number of predefined tests such as TCP and UDP throughput tests and can provide detailed information about network latency and jitter.
3. **Ping and Traceroute**: While they are not benchmarks in the traditional sense, ping and traceroute are often used in network diagnostics to measure round-trip time for packets and to trace the route packets take to reach a destination. They can provide useful information for understanding network latency and routing issues.

