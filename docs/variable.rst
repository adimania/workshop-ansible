Variables
=========

There are times when we have a bunch of similar servers but they are not exactly the same. For example, consider webservers. They may all run Nginx and might have same set of users accounts and ACLs but they may vary slightly in configuration. For such scenarios, variables are very helpful. A variable name can only consist of letters, numbers, and underscores and should always start with a letter. Below is an example of a variable definition in a playbook.

.. code-block:: guess

  - hosts: webservers
    vars:
      http_port: 80
