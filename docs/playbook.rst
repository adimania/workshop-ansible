Playbooks
=========

Playbooks are a description of policies that you want to apply to your systems. It consists of a listing of modules that and the arguments that will run on your system so that it can read the required state. They are written in YAML. It begins with "---", followed by the group name of the hosts where the playbook would be run.

Example:

.. code-block:: guess

   ---
   hosts: localhost

   - name: install nginx
     yum: pkg=nginx state=installed

The example above will install Nginx on our systems. Let us also install pip, flask and our flask app.

.. code-block:: guess

   ---
   hosts: localhost

   - name: install nginx
     yum: pkg=nginx state=installed

   - name: install pip
    yum: pkg=python-pip state=installed

   - name: install flask
     pip: name=flask

   - name: fetch application
     git: repo=https://gist.github.com/c454e2e839fcb20605a3.git dest=flask-demo 

Now we should also copy the config file for Nginx and systemd service file for our flask app. We will also define a couple of handlers. Handlers are executed if there is any change in state of the task which is supposed to notifies them.

Our final playbook would look something like this:

.. code-block:: guess

   ---
   - hosts: localhost
   sudo: yes

   tasks:
     - name: install nginx
       yum: pkg=nginx state=installed

     - name: serve nginx config
       copy: src=../files/flask.conf dest=/etc/nginx/conf.d/
       notify:
       - restart nginx

     - name: install pip
       yum: name=python-pip state=installed

     - name: install flask
       pip: name=flask

     - name: serve flask app systemd unit file
       copy: src=../files/flask-demo.service dest=/etc/systemd/system/

     - name: fetch application
       git: repo=https://gist.github.com/c454e2e839fcb20605a3.git dest=/opt/flask-demo
       notify:
       - restart flask app

   handlers:
     - name: restart nginx
       service: name=nginx state=restarted

     - name: restart flask app
       service: name=flask-demo state=restarted

