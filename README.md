# **Group 2 - CEPARCO Integrating Project**
## **GROUP 2 - S11**

**MEMBERS:**

- Alfred Bastin S. Agustines
- Allan David C. De Leon
- Michael Angelo Depasucat
- Kai Hiori J. Padilla

---

## **Project Overview**
This project involves implementing and comparing the performance of four versions of a kernel:
1. **C Program - Single Query & Multiple Reference**
2. **C Program - Multiple Query & Multiple Reference**
3. **CUDA - Single Query & Multiple Reference**
4. **CUDA - Multiple Query & Multiple Reference**

The program utilizes DNA datasets sourced from the National Center for Biotechnology Information (NCBI), while the query DNA datasets are synthetically generated. All datasets are stored in FASTA format, ensuring easy access and readability without requiring multiple text files.

---
### **i.) Youtube Video**
[Group 2 Presentation]([link here](https://youtu.be/fyQiI6febiI))

---
### **ii.) Screenshot of the Program Output with execution time**

|    C- Single Query & Multiple Reference   |  C- Multiple Query & Multiple Reference   |
| ----------------------------------------- | ----------------------------------------- |
|  <img src="https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/4c8a941a1cb7277bfbdd0dc9e6583f211c4f68b4/image/C-sq-mr.png" alt="image alt" width="500"> | <img src="https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/b781e3793e56de4a8152779d2b5f08ce458980aa/image/C-mq-mr.png" alt="image alt" width="500"> <br><img src="https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/499c65b8534ebe1c434a72df68360d1b8701d1b0/image/Cmm-new.png" alt="image alt" width="500"> |

|    CUDA- Single Query & Multiple Reference   |  CUDA- Multiple Query & Multiple Reference   |
| ----------------------------------------- | ----------------------------------------- |
|  <img src="https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/4c8a941a1cb7277bfbdd0dc9e6583f211c4f68b4/image/CUDAsm-result.png" alt="image alt" width="500"> | <img src="https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/1cd45b8688a66018a3249561df18c9d5018b4e41/image/CUDAmm-result.png" alt="image alt" width="500"><br><img src="https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/1cd45b8688a66018a3249561df18c9d5018b4e41/image/CUDAmm-new.png" alt="image alt" width="500"> |

---
### **iii.) Screenshot of the Code (C)**

|    C- Single Query & Multiple Reference   |  C- Multiple Query & Multiple Reference   |
| ----------------------------------------- | ----------------------------------------- |
| ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/fab0f8de8ab8d70c1875c4f52f924e664517d57c/image/Csqmr-levCode.png) ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/c6072b6269867522ba91176e041ca585818046b6/image/Csqmr-main.png) | ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/fab0f8de8ab8d70c1875c4f52f924e664517d57c/image/Csqmr-levCode.png) ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/c6072b6269867522ba91176e041ca585818046b6/image/Cmqmr-main.png) |

This section shows the main code of the sequential C implmentation of Hyyro's bit-vector algorithm for both single query and multiple query multiple reference examples. The main algorithm of Hyyro is found in the bit_vector_levenshtein function. This c implementation of the algorithm will also serve as the correctness checker for the CUDA implementation of the algorithm.  

---
### **iv.) Screenshot of the Code with correctness check (CUDA)**

|    CUDA- Single Query & Multiple Reference   |  CUDA- Multiple Query & Multiple Reference   |
| ----------------------------------------- | ----------------------------------------- |
|  ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/486e7d6647b942f86c2d5972733227d5563c80a2/image/CUDAsm-lev.png) ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/486e7d6647b942f86c2d5972733227d5563c80a2/image/CUDAsm-kernel.png) ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/486e7d6647b942f86c2d5972733227d5563c80a2/image/CUDAsm-error.png) | ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/a984ccb99568fe0d70b64c7ecb4c09caac8da6c2/image/CUDAmm-lev.png) ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/4c8a941a1cb7277bfbdd0dc9e6583f211c4f68b4/image/CUDAmm-kernel.png) ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/4c8a941a1cb7277bfbdd0dc9e6583f211c4f68b4/image/CUDAmm-error.png) |

This section shows the parallelized implementation of the algorithm in CUDA. The way that it parallelizes the code is through the use of threads, separating the reference DNA and the query DNA per thread for parallelized execution. The CUDA code implements a form that is similar to that of loop unrolling, where each entry reference DNA is divided onto the threads to make it execute multiple reference DNA in a single pass. Instead of 1 algorithm running all of the data sequentially, it can now execute multiple data at the same time in parallel, thus reducing the number of times that the algorithm needs to execute. 

---

### **v.) Comparative Table of Execution Time and Analysis of the Performance of the Kernel**

# Performance Comparison: C vs. CUDA

| Implementation                                  | Average Execution Time (ms) | Error(s) | Loops | No. of Queries | No. of References | Speedup Ratio |
|-------------------------------------------------|--------------------|---------|-------|------------|------------|------------|
| **C (Single Query & Multiple Reference)**       |      20.6381             |     0   |   10   |      1     |     87     |  1x |   
| **C (Multiple Query & Multiple Reference [3] )**     |           57.957         |     0   |   10   |      3     |     87     | 1x |
| **C (Multiple Query & Multiple Reference [10] )**     |           164.0482         |     0   |   10   |      10     |     87     | 1x |
| **CUDA (Single Query & Multiple Reference)**    |         4.1042           |     0   |   10   |      1     |      87     | 5.0285x |
| **CUDA (Multiple Query & Multiple Reference [3] )**  |         3.7719           |     0   |   10   |      3     |      87    | 15.3655x |
| **CUDA (Multiple Query & Multiple Reference [10] )**  |         4.1299           |     0   |   10   |      10     |      87    | 39.722x |

# Speedup Ratio: C vs. CUDA

| Implementation                                  | Speedup Ratio |
|--------------------------------------------------------|------------|
| **C vs CUDA (Single Query & Multiple Reference)**      | 5.0285x | 
| **C vs CUDA(Multiple Query & Multiple Reference [3] )**     | 15.3655x |
| **C vs CUDA(Multiple Query & Multiple Reference [10] )**     |  39.722x |

Length of References: 5k - 17k characters
## Analysis

Based on the results, the performance of the CUDA program with parallelization is faster than the C program for both single query and multiple query versions. The CUDA implementation of the program for single query and multiple reference is 5.0285 times faster that the implementation in C. Similarly, the CUDA code for multiple query and multiple reference is 15.3655 times faster than the C implmentation with 3 queries. The execution time for a dataset of 10 queries give a speedup time of 39.722 times when compared to the time of the C implmentation. These results prove that as the number of data to be processed increases, through query or through reference count, the speedup of the parallel execution when compared to the sequential execution increases. This shows that the sequential execution of the code struggles as the data increases, showing an almost exponential increase in processing times. The parallelized implementation of the data, on the other hand, is shown to be in a similar range in its implementation of the multiple queries. These results can prove that the amount of data that being processed is being handled well by the CUDA program and there is not any noticeable increase in the execution time in that data range. The lack of noticeable increase in the execution time could mean that the CUDA program is still not utililzing all of the threads that were set, showcasing that it is still able to handle the increase in the amount of data to process.

---
### **vi.) Discussion**

During the creation of this project, there were many struggles that the group faced. The first struggle we faced is with the translation of the algorithm into code, where the results we had were uncertain. Throughout the further implementation of the project, specifically in the creation of the parallelized CUDA code. The group did a lot of testing to find out what method of parallelization will be used. in the end, we decided on a parallelized implementation of the program through the use  of multiple threads exeucting all at the same time. Additionally, we also struggled in the implementation of the kernel and the general speeding up of the CUDA program. 

In our implementation of the kernel, we optimized its parameter passing, memory allocation, how it adds parameters to the algorithm, and its acquisition of datasets. These aspects of the CUDA program, although not directly related to our main way of parallelizing the code, adds to the increase in the performance of the program. Every small detail the the group could optimize shaved the execution times, going down from a previous execution time of 7ms-9ms to the current 4ms time.


