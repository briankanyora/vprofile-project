# vprofile-project
## Overview 
Welcome to the vprofile project! This project aims to enhance your DevOps skills by setting up a multi-tier web application stack manually and automating the process using Vagrant. The project will run on a virtual machine (VM) and includes services such as NGINX, Tomcat, RabbitMQ, Memcached, and MySQL, configured to provide a seamless web app experience.

## Vprofile Project Detail
In this project the user will open the url but in this project the url is not set up so we will use the IP address to access the web application. We use the IP address of load balancer where nginx will provide this load balancing experience. Nginx is a web service just apache httpd commonly used as a load balancer. In this project nginx will configured in a way as soon as a request is done it will direct it to the tomcat server /apache tomcat service. Tomcat in this project will be hosting our java web app service. Moreover, tomcat is famously know for hosting a lot of java web application services. Furthermore, if your app needs external storage you can use nfs service. Research what NFS service / Shared storage is? For this project all the data will be stored in mysql services. The RabbitMQ service is a dummy in this project it has no functionality, its been a added for a bit complexity but it a message broker / queueing agent used to connect two app together to stream data form it. In this project when user logins in first the app will first a query to mysql database an retrieve the data and check if the details much but in this project we have added in memcache, where the request will first go to memcache service, where memcache is the database caching which will be connected with mysql server. First time round the users data will be stored in mysql server to the tomcat server then it will be cached in memcache then the second time round for the same request and then it will be accessing the data cached in memcache service. As seen in the image this how the entire stack will be functioning. 


For the automation stack 

Vagrant will be used to automate the vm and this will achieved by vagrant communicating with virtual box and then use bash script to set up our services.

### Flow of execution:
1. Clone source code
2. cd into vagrant dir
3. Bring up vms
4. Validate 
5. Setup all the services 
 - NGINX
 - Memcached
 - RabbitMQ
 - Tomcat
 - App build and deploy
 - Verify from browser 


## Prerequisites
Before getting started, ensure that you have the following tools installed:

 - Hypervisor: Oracle VM Virtualbox
 - Automation: Vagrant
 - IDE: VS Code or any IDE you are comfortable with

### Install Required Tools:
 - Oracle VM Virtualbox (https://www.virtualbox.org)
 - Vagrant (https://www.vagrantup.com)
 - Homebrew (https://brew.sh)

### Project Services
 - NGINX
 - TOMCAT
 - RABBITMQ
 - MEMCACHED
 - MYSQL

To manually set up the project:

1. Provision a VM: Set up a virtual machine using Oracle VM Virtualbox.
2. Service Configuration: Manually configure NGINX, Tomcat, RabbitMQ, Memcached, and MySQL to work together to provide the desired web app experience.



