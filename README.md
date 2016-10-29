# Seed Project for RabbitMQ via ( Vagrant )

Written by Philip A Senger

[philip.a.senger@cngrgroup.com](mailto:philip.a.senger@cngrgroup.com) |
mobile: 0404466846 |
[CV/Resume](http://www.visualcv.com/philipsenger) |
[blog](http://www.apachecommonstipsandtricks.blogspot.com/) |
[LinkedIn](http://au.linkedin.com/in/philipsenger) |
[twitter](http://twitter.com/PSengerDownUndr)

### About

This project contains a Vagrant controlled Sun Virtual Machine with a Puppet recipe to build a server based on CentOS 6 with RabbitMQ and RabbitMQ Web Management. 

### Why

If you are reading this, you may be wonder why I built this project. Using a Message Queue is vital to creating an elastic and high availability systems. It allows the decoupling of components in a n-tier fashion. For example it allows cpu intensive components to be decoupled from the lower demanding cpu components. This allows infrastructure to provision more costly equipment to where it is needed.

This is my seed project based off of many other projects I have seen on the web. I use this as a git submodule for many other projects.

### Install

* Download and install [Vagrant](https://www.vagrantup.com/downloads.html)
* Download and install  [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* Clone the project ```git clone https://github.com/psenger/vagrant-rabbitmq.git```
* In the project dir run ```vagrant up```

Optionally, the VM will use the `vagrant-hostmanager` plugin if it is installed.

    vagrant plugin install vagrant-hostmanager


### Installed Services

#### RabbitMQ

host: localhost  
port: 5672  

#### RabbitMQ Web client

url: http://localhost:15672/  
username: guest  
password: guest  


#### Puppet

Puppet manifests are applied during `vagrant provision`. To manually apply manifests on the VM, run:

    sudo puppet apply --modulepath=/vagrant/puppet/modules/forge:/vagrant/puppet/modules/custom  /vagrant/puppet/manifests

To view currently enabled RabbitMQ plugins, run on the VM:

    sudo puppet resource rabbitmq_plugin --modulepath=/vagrant/puppet/modules/forge:/vagrant/puppet/modules/custom

