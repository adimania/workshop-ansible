Basics of Ansible
================

What is Ansible?
----------------
Ansible is a modern automation tool which makes your life easier by managing your servers for you. You just need to define the configuration in which you are interested and ansible will go ahead and do it for you, be it installing a package or configuring a server application or even restarting a service. Ansible is always ready to manage your servers.

Why do we need it?
------------------
Managing a server is easy. Managing 5 is do'able. Managing hundreds or more is a painful task without automation. Ansible is designed to be simple and effective. You can create identical, replicable servers and clusters of servers in painless and reliable manner.

What are the advantages of using it?
-----------------------------------
Ansible is agentless. You do not need to have anything installed on the client's end. However both push and pull mode are supported. Ansible is a security focused tool. It uses OpenSSH as transport protocol. Ansible scripts (commonly known as playbooks) are writting in yml and are easy to read.

How to install Ansible?
-------------------------
We will install the Ansible by pip. Package managers like dnf, yum and apt can be used but usually pip provides latest version. 

* On Fedora machines:

.. code-block:: none
  
  # dnf install python-pip python-devel git
  # dnf groupinstall "Development Tools"
  # pip install ansible 

* On Centos machines

.. code-block:: none
  
  # yum install epel-release
  # yum install python-pip python-devel git
  # yum groupinstall "Development Tools"
  # pip install ansible 
