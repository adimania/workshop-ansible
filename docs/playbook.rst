Playbooks
=========

Playbooks are a description of policies that you want to apply to your systems. It consists of a listing of modules that and the arguments that will run on your system so that it can read the required state.

Example:

.. code-block:: guess

   - name: install nginx
     yum: pkg=nginx state=installed

The example above will install Nginx on our systems. Let us also install pip, flask and our flask app.

.. code-block:: guess

  - name: install pip
    yum: pkg=python-pip state=installed

  - name: install flask
    pip: name=flask

  - name: fetch application
    git: repo=https://gist.github.com/c454e2e839fcb20605a3.git dest=flask-demo 
