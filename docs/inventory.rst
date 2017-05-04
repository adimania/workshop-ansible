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

There are times when you would want to pull the inventory from a cloud provider, or from LDAP, or you would want the inventory list to be generated using some logic, rather than from a simple text-based inventory list. For such purposes, we can use Dynamic Inventory, but that's a topic for another day.
