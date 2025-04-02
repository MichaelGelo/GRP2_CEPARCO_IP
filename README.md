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
[Group 2 Presentation](link here)

---
### **ii.) Screenshot of the Program Output with execution time**

|    C- Single Query & Multiple Reference   |  C- Multiple Query & Multiple Reference   |
| ----------------------------------------- | ----------------------------------------- |
|  ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/4c8a941a1cb7277bfbdd0dc9e6583f211c4f68b4/image/C-sq-mr.png) | ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/b781e3793e56de4a8152779d2b5f08ce458980aa/image/C-mq-mr.png) |

|    CUDA- Single Query & Multiple Reference   |  CUDA- Multiple Query & Multiple Reference   |
| ----------------------------------------- | ----------------------------------------- |
|  ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/4c8a941a1cb7277bfbdd0dc9e6583f211c4f68b4/image/CUDAsm-result.png) | ![image alt](https://github.com/MichaelGelo/GRP2_CEPARCO_IP/blob/4c8a941a1cb7277bfbdd0dc9e6583f211c4f68b4/image/CUDAmm-result.png) |

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

| Implementation                                  | Average Execution Time (ms) | Error(s) | Loops | No. of Query | No. of Reference |
|-------------------------------------------------|--------------------|---------|-------|------------|------------|
| **C (Single Query & Multiple Reference)**       |      20.6381             |     0   |   10   |      1     |     87     |     
| **C (Multiple Query & Multiple Reference)**     |           57.957         |     0   |   10   |      3     |     87     |
| **CUDA (Single Query & Multiple Reference)**    |         4.1042           |     0   |   10   |      1     |      87     |
| **CUDA (Multiple Query & Multiple Reference)**  |         3.7719           |     0   |   10   |      3     |      87    |

## Analysis

Description here

---
### **vi.) Discussion**

Description here


