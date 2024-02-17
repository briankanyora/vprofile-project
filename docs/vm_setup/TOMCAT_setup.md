Login to the tomcat vm
```
$ vagrant ssh app01
```
Verify Hosts entry, if entries missing update the it with IP and hostnames
```
# cat /etc/hosts
```
Update OS with latest patches
```
# yum update -y
```
Set Repository
```
# yum install epel-release -y
```
Install Dependencies
```
# dnf -y install java-11-openjdk java-11-openjdk-devel
# dnf install git maven wget -y
```
Change dir to /tmp
```
# cd /tmp/
```
