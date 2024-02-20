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
Download & Tomcat Package
```
# wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.75/bin/apache-tomcat-9.0.75.tar.gz
# tar xzvf apache-tomcat-9.0.75.tar.gz
```
Add tomcat user
```
# useradd --home-dir /usr/local/tomcat --shell /sbin/nologin tomcat
```
Copy data to tomcat home dir
```
# cp -r /tmp/apache-tomcat-9.0.75/* /usr/local/tomcat/
```
Make tomcat user owner of tomcat home dir
```
# chown -R tomcat.tomcat /usr/local/tomcat
```
Setup systemctl command for tomcat
Create tomcat service file
```
# vi /etc/systemd/system/tomcat.service
```
Update the file with below content
```
[Unit]
Description=Tomcat
After=network.target
[Service]
User=tomcat
WorkingDirectory=/usr/local/tomcat
Environment=JRE_HOME=/usr/lib/jvm/jre
Environment=JAVA_HOME=/usr/lib/jvm/jre
Environment=CATALINA_HOME=/usr/local/tomcat
Environment=CATALINE_BASE=/usr/local/tomcat
ExecStart=/usr/local/tomcat/bin/catalina.sh run
ExecStop=/usr/local/tomcat/bin/shutdown.sh
SyslogIdentifier=tomcat-%i
[Install]
WantedBy=multi-user.target
```
