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
In order to make your life easier, I package all file you need for homework1. But we need to install git first:

	apt-get install git

please run:

	git clone https://github.com/Hadoop-bigdata/study.git && mv study/homework1 . && rm -r study && chmod u+x homework1/map.py homework1/reduce.py
And then we can find the "homework1" on the current path:

	ls
	
	
# 3. Run MapReduce in Python code
<br>Now the hadoop cluster is running, let's try to write the first python code by hadoop-streaming.</br>
Then we go to the folder we create:


	cd homework1
	
Now let's check whether the codes can run locally:

	cat alphabets.txt | ./map.py | sort | ./reduce.py

	
	
Hadoop Streaming:

	hadoop jar /usr/local/hadoop/share/hadoop/tools/lib/hadoop-streaming-2.7.2.jar -mapper map.py -reducer reduce.py -file map.py -file reduce.py -input alphabets.txt -output output
	
	
