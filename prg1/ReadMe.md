 
# 1. Hadoop MapReduce Record Count

This repository demonstrates how to compile and run a Hadoop MapReduce job to count records in a CSV file.

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
javac -classpath $(hadoop classpath) -d folder RecordCountMapper.java RecordCountReducer.java RecordCount.java
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
yarn jar recordcount.jar (<packagename>).RecordCount /input /output
 ``` 

### 7.Display the contents of the output file:

 
 ```
hdfs dfs -ls /output
hdfs dfs -cat /output/part-r-00000
 ```
