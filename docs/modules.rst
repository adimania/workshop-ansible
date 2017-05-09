Modules
=======

Modules are the executable plugins that get the real job done.

Usually modules can take "key=value" arguments and run in customized way depending up on the arguments themselves.

A module can be invoked from commandline or can be included in an Ansible playbook.

We will discuss playbooks in a minute but for now, let us see modules in action.

To use modules from the command line, we write ansible ad-hoc commands, like the following -

.. code-block:: none

   $ ansible all -m ping

Above example will use the ping module to ping all the hosts defined in the inventory. There are several modules available in ansible. Let us try another one.

.. code-block:: none

  $ ansible webservers -m command -a "ls"

In the above example, we use command module to fire ls command on the webservers group.

.. code-block:: none

  $ ansible -i inventory all -m command -a "iptables -F" --become --ask-become-pass

Here, we use the `command` module to flush iptables rules on all the hosts in the inventory, and we tell ansible to execute the command with sudo privileges using `--become` and ask us the sudo password using `--ask-become-pass`.


.. code-block:: none

  $ ansible all -m setup

Ansible gathers facts about the hosts the tasks are being run against, which can be used later in the playbook execution, we can see all facts using the command above.

See how to extract particular facts in the documentation of `setup` module. To see the documentation, run -

.. code-block:: none

  $ ansible-doc setup

Using `ansible-doc <module name>` we can check the documentation of any ansible module.

