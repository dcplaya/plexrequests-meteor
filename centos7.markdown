---
layout: default
title: CentOS 7
permalink: /centos7/
---


# How To Install PlexRequests On CentOS 7

Below is a guide on how to install PlexRequests on a CentOS 7 minimal install. If you are running a more featured install, some packages may already be installed for you. This guide assumes a clean CentOS 7 has been installed. 

1. For CentOS 7 minimal, some useful things I like to install are below. These are not required but are very helpful.

```bash
sudo yum install net-tools yum-utils nano bash-completion
```

2. Disable SELinux. If you know (or want) to have PlexRequests work with SELinux, then this step would be slightly different. A reboot is required for this to take effect. Set

```bash
SELINUX=disabled
```

in the selinux file

```bash
sudo nano /etc/sysconfig/selinux
sudo reboot
```

3. Enable the EPEL repo

```bash        
sudo  rpm -Uvh http://download.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm
```

4. Install MongoDB
  1. Add MongoDB repo

```bash
sudo nano /etc/yum.repos.d/mongodb.repo
```

  2. Copy and past the following into the mongodb.repo file

```bash
[mongodb]
name=MongoDB Repository
baseurl=http://downloads-distro.mongodb.org/repo/redhat/os/x86_64/
gpgcheck=0
enabled=1
```

  3. Update your yum repo database

```bash
sudo yum update
```

  4. Install the MongoDB and verify it starts

```bash
sudo yum install -y mongo-10gen mongo-10gen-server
sudo service mongod start
```

  5. Set MongoDB to start at boot

```bash
sudo chkconfig mongod on
```

4. Install Node.js
5. Install Meteor

   1. Meteor is simple installed by running
```bash
curl https://install.meteor.com/ | sh
```

6. Install Git and set it up
7. Git clone PlexRequest
8. Open port 3000 in firewalld
9. Start PlexRequest to verify it runs
10. Set PlexRequest to start at boot
