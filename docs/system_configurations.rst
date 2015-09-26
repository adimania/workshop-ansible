System Configurations
=====================

Important modules
-----------------

* Software installation: yum, apt, pip
* Services management: service
* Selinux management: selinux
* User manamgement: user

Examples:

.. code-block:: guess

   - name: install git 
     yum: pkg=git state=installed

   - name: start nginx
     service: name=nginx state=started

   - name: put selinux to enforcing mode
     selinux: policy=targeted state=enforcing

   - name: create the user
     user: name=aditya
