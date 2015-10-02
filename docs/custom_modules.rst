Custom Modules
==============

Let we try to build a very basic module which will get and set system time. We
will do it in step by step.

* Write a python script to get current time and print json dump.
* Write a python script to get time as argument and set it to system.


Test Module
-----------

::

    git clone https://github.com/ansible/ansible.git --recursive
    source ansible/hacking/env-setup
    chmod +x ansible/hacking/test-module

    ansible/hacking/test-module -m ./timetest.py

    $ hacking/test-module -m workshop-ansible/code/timetest.py
    * including generated source, if any, saving to:
      /home/prkumar/.ansible_module_generated
      * this may offset any line numbers in tracebacks/debuggers!
        ***********************************
        RAW OUTPUT
        {"time": "2015-09-03 12:08:40.569710"}


      ***********************************
      PARSED OUTPUT
      {
          "time": "2015-09-03 12:08:40.569710"
      }


If you don't get any desired output then you might have to check your test
module code again.

Read Input
++++++++++

We will pass a key value pair (time=<string>) to module and check if we are able
to set time for a system.

Let's set time to "Oct 7 10:10"

* update timetest.py with latest changes (check in code directory)


::

    $ hacking/test-module -m workshop-ansible/code/timetest_update.py -a "time=\"May 7 10:10\""
    * including generated source, if any, saving to:
      /home/prkumar/.ansible_module_generated
      * this may offset any line numbers in tracebacks/debuggers!
        ***********************************
        RAW OUTPUT
        Thu May  7 10:10:00 IST 2015
        {"msg": "failed setting the time", "failed": true}

      date: cannot set date: Operation not permitted

      ***********************************
      INVALID OUTPUT FORMAT
      Thu May  7 10:10:00 IST 2015
      {"msg": "failed setting the time", "failed": true}


`source <http://docs.ansible.com/ansible/developing_modules.html#tutorial>`_

`Example <https://github.com/rishabhdas/dmidecode-ansible>`_
