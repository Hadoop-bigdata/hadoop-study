# How to run docker for HW1
I try to run the related command step by step so that you could save more time on your coding.
<br></br>
## 1. Enter the hadoop cluster

### 1.1 restart hadoop virtual machine in docker
When you shut down or restart your laptop, your docker and all virtual machines above it would shut down at the same time.
Thus if you want to run hadoop master, please restart 3 virtual machines (1 master, 2 slaves) on docker first:

	docker start hadoop-master hadoop-slave1 hadoop-slave2
<br></br>
### 1.2 attach to the hadoop-master container
Because we have 3 machines running on docker, we need to tell docker which one we want to control in bash command:

	docker exec -ti hadoop-master bash
<br></br>
### 1.3 restart hadoop cluster on 3 virtural machine
Now we are in the hadoop-master machine (container), and then we need to tell the master we want to start the hadoop cluster and connect all 3 manchine together:

	./start-hadoop.sh
	
or we can run in it in 2 command:

	start-dfs.sh
	start-yarn.sh
<br></br>
### 1.4 check whether hadoop is running 

	hadoop fs -ls
If you found error in this command, I will suggest you to restart the docker or your laptop.
Or maybe you haven't finished installing the hadoop cluster, you can see here:
https://github.com/Hadoop-bigdata/study/blob/master/README.md
<br></br>
	
# 2. Download the homework files
<br>In order to make your life easier, I package all file you need for homework1.</br>
<b>Hint: Step 2 just need to run once.</b>
<b>If you could not run your code in the last lesson, I recommend you to do it again as below.</b>

## 2.1 install git command
We need to install git first:

	apt-get update && apt-get install git
<br></br>
## 2.2 download homework files in github:
	git clone https://github.com/Hadoop-bigdata/study.git && mv study/homework1 . && rm -r study && chmod u+x homework1/map.py homework1/reduce.py
And then we can find the "homework1" on the current path and go to it:

	ls
	cd homework1
	
## 2.3 save text files to hdfs:
The alice.txt is used for homework, let's try to move it to hdfs.

	hadoop fs -put alice.txt input
	
# 3. Run MapReduce in Python code

## 3.1 go into the homework1 folder
<br>Now all the files have been downloaded, lets go to homework1 folder and see what in it:


	cd homework1
	ls
<br></br>
## 3.2 check your code in local
<br><b>Important:</b> please try to debug your code first in this mode after writing python code.</br>
Now let's check whether the codes can run locally:

	cat alice.txt | ./map.py | sort | ./reduce.py
If you found any error in this mode, it means your code has something wrong. Please go back to check and debug your code.
<br></br>
## 3.2 check your code in hadoop cluster
Now our code can run on the local mode, let's move on to run on hadoop cluster.


	hadoop jar /usr/local/hadoop/share/hadoop/tools/lib/hadoop-streaming-2.7.2.jar -mapper map.py -reducer reduce.py -file map.py -file reduce.py -input input/alice.txt -output output

<br><b>please check the setting is right.</b></br>
-mapper: which local python file you want to use as map function

-reducer: which local python file you want to use as reduce function

-file: which files you want to sent to your datanode.

-input/output: the HDFS path and files you want read and write.
<br></br>

## 3.2 check your answer in hdfs
<br>If our job is successful, we can see what in the output folder.</br>
<br>Please notice that your output folder is where you set above.</br>

	hadoop fs -ls output
<br> Then we use cat command to see the output.</br>

	hadoop fs -cat output/part-00000
	<br></br>
# 4. Run MapReduce in Java code
For some students, maybe they want to write in the java code. Let's see how to run java code here.

## 4.1 write and save your code in java file
You can write your own code from the example, WordCount.java. Here I will use it as example.
For more detail, pleas go to the blackboard and find it in the Mapreduce slide.
<br></br>
## 4.2 write and save your code in java file
Set environment variable to find libraries and denpendence.
	
	export HADOOP_CLASSPATH=${JAVA_HOME}/lib/tools.jar
<br></br>	
## 4.3 Create jar file
Then we create wc.jar file

	hadoop com.sun.tools.javac.Main WordCount.java
	jar cf wc.jar WordCount*.class
<br></br>
## 4.4 Run Mapreduce
Now we can run Mapreduce job, please specify your main running class, input and output path

	hadoop jar wc.jar WordCount input/alice.txt output
<br></br>
## 4.5 check your answer on hdfs
Now we can check our answer in the folder where we set above.

	hdfs dfs -ls output
	hdfs dfs -cat output/part-r-00000

# 5 Download your code and output to your laptop
Now you might have finished the homework and want to download the files back to your laptop.

## 5.1 get output from hdfs
I just give an example here. Please set your own output file path.

	hadoop fs -get output/part-00000
	
## 5.2 get the local path
If you still in the homework1 folder, you don't need to do this step.
If not, please type:

	pwd
## 5.3 download the files to your local laptop
Please open a new terminal/docker quickstart terminal, and then type:

	docker cp hadoop-master:/root/homework1 "e:/study/bigdata_programming/homework1"
<br>If you are not in the homework1 folder, please change the "/root/hoework1" to the path you get in last step.</br>
<br>The path "e:/study/bigdata_programming/homework1" is my laptop location, you can change and use your own.</br>
