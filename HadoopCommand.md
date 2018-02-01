# The Hadoop basic command
<br>The hadoop command is quite similar to the bash command, if you learn the bash command before. Its format is simple.</br>
<br>For example:</br>

	hadoop fs -cp a.txt b.txt
<br>It means that you are telling hadoop fileSystem to copy <b>a.txt</b> to <b>b.txt</b></br>
<br>The hadoop fileSystem would regard your file/folder in your home directory, if you don't specify the absolute path.</br>
##
### 1 create a new folder
<br>We try to create a new folder "input" under our home directory.</br>
<br>We can type:</br>

	hadoop fs -mkdir input
	
or the whole path:

	hadoop fs -mkdir /user/yourUserName/input
<br> Please notice the "yourUserName" should be the excat username, in our study environment, it's "root".</br>
##
### 2 List the directory
<br>If you want to see what kinds of files and folder in your home directory.</br>
<br>Then we can type:</br>

	hadoop fs –ls
<br> If you want to see more specific path.</br>
<br>We can try like:</br>

	hadoop fs –ls /user/root/input


### 3 copy file from local to HDFS
<br>There are two command can do this thing. One is copyFromLocal, another is put</br>
<br>CopyFromLocal is more strict than put, because it just allow send file from local to HDFS.</br>
<br>Suppose you have a file called test.txt, or maybe you create as below, we can try:</br>
	
	echo "HDFS test file" >> test.txt
	hadoop fs -copyFromLocal test.txt
<br>Now the test.txt is in your HDFS home directory, you can check it by ls command mentioned above.</br>
Or we can use put,they are the same:

	hadoop fs -put test.txt input
<br> In this example we put file to HDFS input folder under home dirctory.</br>
### 4 copy file from HDFS to local
<br>It's almost the same as above, but we just change the command from copyFromLocal to copyToLocal

	hadoop fs -copyToLocal test.txt 1.txt
<br>Here we get the file from the HDFS to local linux, and we change its name to 1.txt.</br>
Or we can use get:

	hadoop fs -get test.txt 2.txt

### 5 move file in HDFS
<br>So We can use move command:

	hadoop fs -mv test.txt input/1.txt
<br>If you don't want to delete the original test file, we can use copy command.</br>

	hadoop fs -mv input/1.txt input/2.txt

### 6 find file in HDFS
<br>Sometimes we want to find the path of our file in HDFS, we can try:

	hadoop fs -find -name 1.txt

### 7 check the status of HDFS
<br>If we are wondering whether our Hadoop filesystem is healthy, we can type:

	hadoop fsck /user
or:

	hdfs fsck /user

### 8 Running Mapreduce by Hadoop-Streaming
<br>We want to use python to run mapreduce, while the original mapreduce just support Java. Thus we use some tools to help us translate the python language, that is Hadoop-Streaming.</br>
The format of running Hadoop-Streaming is like this:

	hadoop jar /usr/local/hadoop/share/hadoop/tools/lib/hadoop-streaming-2.7.2.jar -mapper map.py -reducer reduce.py -file map.py -file reduce.py -input input/purchases -output output

<br>Hints: the path behind "hadoop jar" is the path of hadoop-streaming.</br>
<br>-mapper: which local python file you want to use as map function</br>
<br>-reducer: which local python file you want to use as reduce function</br>
<br>-file: which files you want to sent to your datanode.</br>
<br>-input/output: the HDFS path and files you want read and write.</br>
<br></br>
## Other related tutorial:
<br>Hadoop installation:</br>
https://github.com/Hadoop-bigdata/study/blob/master/README.md
<br></br>
<br>Docker Basic Command:</br>
https://github.com/Hadoop-bigdata/study/blob/master/DockerCommand.md
