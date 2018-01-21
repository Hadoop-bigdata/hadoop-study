# Hadoop-Installation

## 1. Install Docker

### 1.1 Download Docker 
	
Before Download the Docker make sure your computer supports vitrual machine.

For Mac: https://www.docker.com/docker-mac
	
For Windows: https://www.docker.com/docker-windows
	
	
### 1.2 Install Docker on the local machine
	
### 1.3 Set up Docker Environment

	For MAC users:
	
	First, click on Docker logo next to your time clock, then click on preferences.
	In the perferences, click on advanced. 
	
	For Windows users:
	
	We can find the docker logo in the bottom right of the screen, which is also next to your time clock. 
	And then we right click the docker logo, selcet the "Settings", and the click on the "Advanced".
	
	The Docker's default environment CPUs is 2 and Memory is 2GB, while for Hadoop we need to at least
	update the CPUs to 4 and Memory to 4GB for computer.
	Please notice that the Docker preferences depends on your computer.
	The more Memory and CPUs you give to Docker, the faster running speed you have. 
	If the Docker is not running properly, giving more Memory and CPUs can potentially solve the problem.
	
## 2. Pull Hadoop Image in Docker

After install Docker on the local machine, you need to open the terminal (for MAC) or command line (for Windows)
	
### 2.1 Pull Hadoop Image
	

	docker pull hadoopstudy/hadoop_bigdata

Thanks to hadoop study group that has already built the Hadoop image in docker.
	


	
### 2.2 Create clone github file
	
	git clone https://github.com/Hadoop-bigdata/hadoop_study.git
	
For the Mac users, if you meet the error

	xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at : /Library/Developer/CommandLineTools/usr/bin/xcrun

You can try:

	xcode-select –install

After try download the xcode, then type the same code:

	git clone https://github.com/Hadoop-bigdata/hadoop_study.git

	

### 2.3 start the hadoop cluster

	cd hadoop_study
	./start-container.sh

	
If you can't execut the sh file, like some windows system, please execut the command as below:

	docker network create --driver=bridge hadoop
	docker run -itd --net=hadoop -p 50070:50070 -p 8088:8088 -p 8888:8888 --name hadoop-master --hostname hadoop-master hadoopstudy/hadoop_bigdata:latest
	docker run -itd --net=hadoop --name hadoop-slave1 --hostname hadoop-slave1 hadoopstudy/hadoop_bigdata:latest
	docker run -itd --net=hadoop --name hadoop-slave2 --hostname hadoop-slave2 hadoopstudy/hadoop_bigdata:latest
	docker exec -it hadoop-master bash	

	
