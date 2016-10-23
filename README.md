### Introduction

This is a multi-server chat system based on Java which takes security, failure handling and scalability into consideration. Chat servers are deployed on multiple VMs using AWS. A GUI was designed and implemented  to improve user experience. 

All communications between servers and between clients and servers are encrypted via secure channels. There is also an authentication mechanism for user to login to the system with a unique username.

### Server Info

- *central_server*:
  - Public DNS: ec2-54-165-255-160.compute-1.amazonaws.com
  - Public IP: 54.165.255.160
- *chat_server_1*: 
  - Public DNS: ec2-54-166-217-43.compute-1.amazonaws.com
  - Public IP: 54.166.217.43
- *chat_server_2*: 
  - Public DNS: ec2-54-162-109-250.compute-1.amazonaws.com
  - Public IP: 54.162.109.250
- *chat_server_3*: 
  - Public DNS: ec2-54-147-77-104.compute-1.amazonaws.com
  - Public IP: 54.147.77.104

------



### Login to instance 

***central_server***

```shell
ssh -i ~/.ssh/MyFirstKey.pem ubuntu@ec2-54-165-255-160.compute-1.amazonaws.com
```

***chat_server_1***

```shell
ssh -i ~/.ssh/MyFirstKey.pem ubuntu@ec2-54-166-217-43.compute-1.amazonaws.com
```

***chat_server_2***

```shell
ssh -i ~/.ssh/MyFirstKey.pem ubuntu@ec2-54-162-109-250.compute-1.amazonaws.com
```

***chat_server_3***

```shell
ssh -i ~/.ssh/MyFirstKey.pem ubuntu@ec2-54-147-77-104.compute-1.amazonaws.com
```



------

### Install Java

```shell
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

------

### Upload Files

***central_server***

```shell
scp -i ~/.ssh/MyFirstKey.pem -r ~/Desktop/midnight ubuntu@ec2-54-165-255-160.compute-1.amazonaws.com:/home/ubuntu
```

***chat_server_1***

```shell
scp -i ~/.ssh/MyFirstKey.pem -r ~/Desktop/midnight ubuntu@ec2-54-166-217-43.compute-1.amazonaws.com:/home/ubuntu
```

***chat_server_2***

```shell
scp -i ~/.ssh/MyFirstKey.pem -r ~/Desktop/midnight ubuntu@ec2-54-162-109-250.compute-1.amazonaws.com:/home/ubuntu
```

***chat_server_3***

```shell
scp -i ~/.ssh/MyFirstKey.pem -r ~/Desktop/midnight ubuntu@ec2-54-147-77-104.compute-1.amazonaws.com:/home/ubuntu
```



------

### Launch Server

***central_server***

```shell
java -jar aserverjar.jar -k DSk.jks
```

***chat_server_1***

```shell
java -jar serverjar.jar -n s1 -l s1_conf.txt -k DSk.jks
```

***chat_server_2***

```shell
java -jar serverjar.jar -n s2 -l s2_conf.txt -k DSk.jks
```

***chat_server_3***

```shell
java -jar serverjar.jar -n s3 -l s3_conf.txt -k DSk.jks
```
