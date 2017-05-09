Inventory File
==============

Inventory defines the groups of hosts which are alike in any way. For example, you would want to group your web servers in one group and application servers in another. A group can have multiple server and one server can be a part of multiple groups.

Name of group is enclosed in square brackets []. Server names can be their DNS names or IP addresses. 

::

    [webservers]
    server1
    [application]
    server1
    server2

By default, ansible looks for the inventory file at `/etc/ansible/hosts`, but that can be modified by passing a `-i <inventory_path` to the ansible command line.

We can modify the way ansible connects to our hosts by supplying additional information in the inventory file.

::

    [webservers]
    server1 ansible_port=4242 ansible_user=adimania
    [application]
    server1
    server2
    [master]
    localhost ansible_connection=local

A more exhaustive list of inventory parameters can be seen here - http://docs.ansible.com/ansible/intro_inventory.html#list-of-behavioral-inventory-parameters

There are times when you would want to pull the inventory from a cloud provider, or from LDAP, or you would want the inventory list to be generated using some logic, rather than from a simple text-based inventory list. For such purposes, we can use Dynamic Inventory, but that's a topic for another day.
