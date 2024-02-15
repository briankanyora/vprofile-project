Login to the Memcache vm
$ vagrant ssh mc01
Verify Hosts entry, if entries missing update the it with IP and hostnames
```
# cat /etc/hosts
```
Update OS with latest patches
```
# yum update -y
```
Install, start & enable memcache on port 11211
```
# sudo dnf install epel-release -y
# sudo dnf install memcached -y
# sudo systemctl start memcached
# sudo systemctl enable memcached
# sudo systemctl status memcached
# sed -i 's/127.0.0.1/0.0.0.0/g' /etc/sysconfig/memcached
# sudo systemctl restart memcached
```
Starting the firewall and allowing the port 11211 to access memcache
```
# firewall-cmd --add-port=11211/tcp
# firewall-cmd --runtime-to-permanent
# firewall-cmd --add-port=11111/udp
# firewall-cmd --runtime-to-permanent
# sudo memcached -p 11211 -U 11111 -u memcached -d
```
