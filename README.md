# **Daal4py**

## **Benchmarking PyDaal with Scikit-Learn Librar**

To know more about Daal4PY - [link-here](https://intelpython.github.io/daal4py/)

(Data Analytics Acceleration Library by Intel)

The aim of this project is to work on and understand the effect of distributed and multiprocessing on computationally heavy jobs. We perform two case studies - Daal4py and SHAP. Daal4py was created to give data scientists the easiest way to utilize Intel(R) oneAPI Data Analytics Library powerful machine learning building blocks directly in a high-productivity manner. Internally, Daal4py uses Intel(R) one API Data Analytics Library to deliver the best performance. We benchmark the performance with large datasets to see how scalable Daal4py is.

The benchmarking of Daal4py is a part of research under AI Skunkworks, in collaboration with Discovery (Research Computing at Northeastern University). The broad aim of the research is to benchmark PyDAAL(a.k.a. Daal4py) by Intel and compare it with other existing libraries for performance, scalability, and ease of use. This research is undertaken by Abhishek Maheshwarappa and Kartik Kumar. 

To understand the full project go through the report [here](https://github.com/abhi-gm/Fast-Scalable-and-Easy-Machine-Learning-With-DAAL4PY/blob/main/Fast-Scalable-and-Easy-Machine-Learning-With-DAAL4PY-Report.pdf) 

## **Introduction Daal4py**


Daal4py makes machine learning algorithms in Python lightning-fast and easy to use. It provides highly configurable machine learning kernels, some of which support streaming input data and/or can be easily and efficiently scaled out to clusters of workstations. Internally it uses Intel(R) one API Data Analytics Library to deliver the best performance.

## **Motivation**

Daal4py claims to be a faster and efficient way to run machine learning models, be it serial or parallel. The multiprocessing in Daal4py is called distributed computing (single Program Multiple Data - SPMD), which is claimed to be very fast compared to the native Scikit-learn algorithm which uses job lib for parallelism. 

The goal is to test serial and parallel execution of computationally heavy jobs within Daal4py framework. We want to test serial and parallel performance across multiple datasets and various algorithms. 

## **Daal4py methodology**


There are 3 types of data processing in Daal4py. They are: -
1. Batch Processing
2. Stream Processing
3. Distributed Processing

### **Batch Processing***

For small quantities of data, the input data can be inputted all at once using batch processing mode. This is similar to serial processing.

### **Stream Processing**

For large quantities of data, it may be unfeasible to provide all input data at once unlike with batch processing. This might be because the data resides in multiple files and merging it is too costly to deem feasible. In other cases, the dataset may be too large to load completely into memory. The data being processed may also be an actual stream. Daal4py’s streaming mode allows one to process these types of data in a quick and easy manner.

### **Distributed Processing**

Daal4py operates in Single Program Multiple Data (SPMD) style, which means your program is executed on several processes (e.g. similar to MPI). The use of MPI is not required for Daal4py’s SPMD-mode to work- all necessary communication and synchronization happens through Daal4py. However, it is possible to use Daal4py and mpi4py in the same program.

## **Result and Analysis**

All time durations shown in graphs are in milliseconds (ms)

**Algorithms and abbreviations:**

LR - Linear regression (daal4py) , RR - Ridge regression (daal4py), Kmeans - KMeans Clustering (daal4py), NB - Naive Bayes (daal4py), PCA Principal Component Analysis(daal4py), SVD - Singular Value Decomposition (daal4py), SK linear - Scikit -learn Linear Regression (sklearn)

![](https://github.com/abhi-gm/Fast-Scalable-and-Easy-Machine-Learning-With-DAAL4PY/blob/main/assest/pasted%20image%200.png)

As seen in the graph above, daal4py algorithms are much faster than Scikit-learn algorithms. Serial vs Parallel yields mixed results across algorithms but the overall time taken is very less

### **Other results**

![](https://github.com/abhi-gm/Fast-Scalable-and-Easy-Machine-Learning-With-DAAL4PY/blob/main/assest/pasted%20image%200%20(1).png)

![](https://github.com/abhi-gm/Fast-Scalable-and-Easy-Machine-Learning-With-DAAL4PY/blob/main/assest/pasted%20image%200%20(2).png)


# **Guide to use the environment and Code**

# **Steps to setup environment to use Daal4py**


1. We have a environment.yml file onb repo locate it.
2. Go to anaconda or miniconda installed on the cluster and create the virtual environment.
3. While creating the environment use yml file provided 
4. Create the environment from the environment.yml file:
```
conda env create -f environment.yml
```
5. Activate the new environment: conda activate myenv
6. Verify that the new environment was installed correctly: 

```
conda env list
```
# **Steps to run the code**

1. Once the environment is set up it will allow you to run both Daal4py and SHAP code.
2. Navigate to the directory containing main.py file
3. There few datasets in the data folder and any other tabular data can be added
4. To run use command 

```
python main.py
```


I would like to thank the RC Discovery team of Northeastern University especially Manasvita Joshi and Mariana Levi for their help and support in getting the environment setup. 
