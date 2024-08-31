 
# Hadoop MapReduce Using Temperature Dataset 

This repository demonstrates how to compile and run a Hadoop MapReduce job to find the maximum temperature by year from a CSV file.

## Prerequisites

Ensure you have the following installed and configured:
- Java Development Kit (JDK)
- Hadoop
- A Hadoop cluster or a local Hadoop setup

## Setup and Execution

 Create a Directory

First, create a directory to store compiled Java classes:

```
mkdir folder
```
### 2.Compile the Java Code
```
javac -classpath $(hadoop classpath) -d folder M1.java R1.java Driver.java
```
 
### 3.Package into a JAR File



 ```
jar -cvf recordcount.jar -C folder/ .
 ```

### 4.Prepare HDFS
 
 ```
hdfs dfs -mkdir /input
 ```

### 5.Upload your CSV dataset to the HDFS input directory:
 ```
 
hdfs dfs -put dataset124.csv /input/data.csv
 ```
 

### 6.Run the MapReduce job using the JAR file:

 
 ```
yarn jar recordcount.jar (<packagename>).Driver /input /output2
 ``` 

### 7.Display the contents of the output file:

 
 ```
hdfs dfs -ls /output2
hdfs dfs -cat /output2/part-r-00000
 ```

### 8.Checking Job Status
check the status of a job using the Hadoop command-line  


 
 ```
hadoop application -status <applicationId>
hadoop job -list
 ```

### 9.Terminating the Job :
To terminate a running job, use the following command:
 


 
 ```
hadoop job -kill $jobId
 ```
