Ansible Vault
=============

This feature of Ansible allows you to keep your sensitive data encrypted like
passwords and keys.

* Ansible provide a command line tool `ansible-vault` for edit sensitive files.
* When you run a playbook then command line flag `-ask-vault-pass` or
  `-vault-password-file` can be used.
* Vault can encrypt any structured data file used by Ansible.

Create Encrypted File
---------------------

::

    ansible-vault create foo.yml

Edit Encrypted File
-------------------

::

    ansible-vault edit foo.yml

Rekeying Encrypted File
-----------------------

::

    ansible-vault rekey foo.yml

View Content of Encrypted File
------------------------------

::

    ansible-vault view foo.yml

Running a playbook with vault
-----------------------------

::

    ansible-playbook site.yml --ask-vault-pass
    ansible-playbook site.yml --vault-password-file ~/.vault_pass.txt
    ansible-playbook site.yml --vault-password-file ~/.vault_pass.py



