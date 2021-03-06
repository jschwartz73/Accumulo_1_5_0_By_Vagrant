# Accumulo v1.5.0 By Vagrant

A three node Accumulo cluster running on Ubuntu Precise (12.04). The instance name is 'instance'. The 
user name is 'root' and the password is 'secret'.

1. Install Vagrant
2. vagrant plugin install vagrant-hostmanager
3. Download this project.
4. Run 'Vagrant up'
5. Run 'post_spinnup.sh'

```
I had trouble getting vagrant to start.
The following steps fixed it:

6.  vagrant ssh master
7.  ./accumulo_home/bin/accumulo/bin/stop-all.sh 
    - Sometimes I have to hit <ctrl>+c to get it to force a shutdown
8.  ./accumulo_home/bin/accumulo/bin/start-all.sh 
9.  <be patient>
```
Now you can visit the following URLs in your browser:

<a href='http://affy-master:50095/'>http://affy-master:50095/</a><br/>
<a href='http://affy-master:50070/dfshealth.jsp'>http://affy-master:50070/dfshealth.jsp</a><br/>
<a href='http://affy-master:50030/jobtracker.jsp'>http://affy-master:50030/jobtracker.jsp</a><br/>

You can SSH to the nodes using the following commands. Notice that the hostnames start with 'affy-' but that 
the vagrant nodes do not have the prefix.

```
vagrant ssh master
vagrant ssh slave1
vagrant ssh slave2
```

## Install Pig on a node

1. vagrant ssh master
2. cd /home/vagrant/accumulo_home/bin
3. tar xvfz /vagrant/files/pig-0.12.0.tar.gz
4. export PATH=/home/vagrant/accumulo_home/bin/pig-0.12.0/bin:$PATH 

If you want pig to always be available update your path in the ~/.bashrc file.


## X-WINDOWS on SLAVE2

The second slave is configured so that X11 port forwarding is automatic when you use 'vagrant ssh slave2'. For 
convenience, I manually installed additional software on that node:

```
sudo apt-get install -y x11-apps
sudo apt-get install -y netbeans
```


