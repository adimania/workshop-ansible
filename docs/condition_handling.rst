Condition handling
==================

Conditionals help us evaluate a variable and take some action on the basis of the outcome.

Example:

.. code-block:: guess

   ---

   - hosts: localhost
     vars:
       - state: false

     tasks:
       - shell: echo good state
         when: state
