Login to the db vm
$ vagrant ssh db01
Verify Hosts entry, if entries missing update the it with IP and hostnames
'''
# cat /etc/hosts
'''
Update OS with latest patches
'''
# yum update -y
'''
Set Repository
'''
# yum install epel-release -y
'''
Install Maria DB Package
'''
# yum install git mariadb-server -y
'''
Starting & enabling mariadb-server
'''
# systemctl start mariadb
# systemctl enable mariadb
'''
RUN mysql secure installation script.
'''
# mysql_secure_installation
'''
NOTE: Set db root password, I will be using admin123 as password
