Playbooks
=========

Playbooks are a description of policies that you want to apply to your systems. It consists of a listing of modules that and the arguments that will run on your system so that it can read the required state.

Example:

.. code-block:: guess

   - name: install nginx
     yum: pkg=nginx state=installed

