Ansible-Workshop
================

This is the asciidoc for the Ansible Workshop @ PyCon 2015, Bengaluru. Useful links:

* Proposal: https://in.pycon.org/cfp/pycon-india-2015/proposals/getting-started-with-ansible/
* Ascii Doc syntax: http://asciidoctor.org/docs/asciidoc-writers-guide
* To setup the laptop to compile asciidoc (Fedora 22 does not work due to a bug in fop):

::

    yum install git asciidoc docbook-xsl fop

Edit /etc/asciidoc/asciidoc.conf and change the following

::

    iconsdir=./images/icons

To:

::

    iconsdir=/etc/asciidoc/images/icons

* To create the pdf:

::

    a2x -fpdf -dbook --fop --no-xmllint -v <asciidoc file>


Read it `here <http://workshop-ansible.readthedocs.org/en/latest>`_.
