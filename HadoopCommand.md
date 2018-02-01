# The Hadoop basic command
<br>The hadoop command is quite similar to the bash command, if you learn the bash command before. Its format is simple.</br>
<br>For example:</br>

	hadoop fs -cp a.txt b.txt
<br>It means that you are telling hadoop fileSystem to copy <b>a.txt</b> to <b>b.txt</b></br>
<br>The hadoop fileSystem would regard your file/folder in your home directory, if you don't specify the absolute path.</br>
##
### 1 create a new folder
<br>Sometimes you might open several containers, but you want to find them out and check them.</br>
<br>Then we can type:</br>

	docker ps -a
<br> You would get all the containers you create, including related message, like nanme or something else.</br>
##
### 2.3 copy file between host and container
<br>Now you want to copy the file from your laptop to your container.</br>
<br>Then we can type:</br>

	docker cp E:\bigdata hadoop-master:\root\try
<br> It means that you copy your local file  E:\bigdata to the container hadoop-master, and save them in the \root\try.</br>
<br>If we type:</br>

	docker cp hadoop-master:\root\try E:\bigdata 
<br> It means that you copy your container's file to your local laptop.</br>

### 2.4 For more docker command
<br>So there are still lots of other command that can help better control the docker.</br>
<br> You can find the official tutorial as below, I hope that can help you.</br>
https://docs.docker.com/engine/reference/commandline/docker/
<br></br>
## Other related tutorial:
<br>Hadoop installation:</br>
https://github.com/Hadoop-bigdata/study/blob/master/README.md
<br></br>
<br>Docker Basic Command:</br>
https://github.com/Hadoop-bigdata/study/blob/master/DockerCommand.md
