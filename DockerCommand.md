# How to use Docker

## 1. Docker and Local host
<br>Basically, docker are trying to virtualize the system based on our laptop, or so-called Host system. These virtualized systems are called container in docker.</br>
<br>For our hadoop program, we try to simulate several containers as the true machines to create hadoop cluster.</br>
<br>Hints: Hadoop basically is the application that install in the Linux System.</br>
<br> The relationship between them should be:</br>
#### Host (our Laptop) -> Container (Linux System) -> Application (Hadoop)
<br> Or maybe the picture as below is easier to understand:

![relationship](https://www.juniper.net/assets/img/misc/diagram-what-is-docker-container.png)




## 2. Docker Basic Command
<br> Docker is quite famous in the market right now. Learning it would not be a bad choice.</br>
<br> Here I will try to introduce some fundamental docker command to help you better handle Docker:</br>

### 2.1 start your container
<br>When you restart your laptop, the docker and all the containers would shut down in the same time.</br>
<br>But you want to run your container again, like our hadoop container, we can type:</br>

	docker start hadoop-master hadoop-slave1 hadoop-slave2
<br> You are telling the docker to start the containers who names are hadoop-master,slave.</br>
<br> You can use the containers' name or ID, they are the same.</br>
##
### 2.2 attach to your container
<br>So now maybe you have already started your container, but you might found that you still not connect to the containers, like Hadoop-Master.</br>
<br>Now we can type:</br>

	docker exec -ti hadoop-master bash
<br> You are telling the docker to exec the container's bash command, so that you can use bash to control the container.</br>
##
### 2.3 list your container
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

## Other related tutorial:
<br>Hadoop installation:</br>
https://github.com/Hadoop-bigdata/study/blob/master/README.md
