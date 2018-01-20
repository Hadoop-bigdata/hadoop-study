# Hadoop-Installation

## 1. Install Docker

* 1.1 Download Docker 
	
	Before Download the Docker make sure your computer supports vitrual machine.

	For Mac: https://www.docker.com/docker-mac
	
	For Windows: https://www.docker.com/docker-windows
	
	
* 1.2 Install Docker on the local machine
	
* 1.3 Set up Docker Environment

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
	
* 2.1 Pull Hadoop Image
	
	```
	$docker pull kiwenlau/hadoop:1.0
	//command to pull Hadoop image into Docker
	```
	Thanks to kiwenlau who has already built the Hadoop image in docker.
	
	Reference: https://github.com/kiwenlau/hadoop-cluster-docker
	
	In project, we will build our Hadoop Environment based on his Hadoop image. 
	
* 2.2 Create clone github file
	
	```
	$git clone https://github.com/Hadoop-bigdata/Hadoop.git
	//command to download the github file into local machine
	```
	For the Mac users, if you meet the error
	```
	xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at : /Library/Developer/CommandLineTools/usr/bin/xcrun
	```
	You can try:
	```
	$xcode-select –install
	//command to download the xcode
	```
	After try download the xcode, then type the same code:
	```
	$git clone https://github.com/Hadoop-bigdata/Hadoop.git
 	```
	
* 2.3 Connect the Hadoop Network

	```
	$docker network create --driver=bridge hadoop
 	//command to create the network to connect the master container with slave container
	```
