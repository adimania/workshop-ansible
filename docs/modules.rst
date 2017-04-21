Modules
=======

Modules are the executable plugins that get the real job done.
Usually modules can take "key=value" arguments and run in customized way depoending up on the arguments themselves.
A module can be invoked commandline or can be included in an Ansible playbook.
We will discuss playbooks in a minute but for now, let us see modules in action.

.. code-block:: none

   $ ansible all -m ping

Above example will use the ping module to ping all the hosts defined in the inventory. There are several modules available in ansible. Let us try another one.

.. code-block:: none

  $ ansible webservers -m command -a "ls"

In Above example, we used command module to fire ls command on the webservers group.
