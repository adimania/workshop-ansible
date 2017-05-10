Playbooks
=========

Playbooks are a description of policies that you want to apply to your systems. They consist of a listing of modules and the arguments that will run on your system so that ansible gets to know the current state. They are written in YAML. They begin with "---", followed by the group name of the hosts where the playbook would be run.

Example:

.. code-block:: guess

   ---
   hosts: localhost

   - name: install nginx
     yum: name=nginx state=installed

The example above will install Nginx on our systems. Let us also install pip, flask and our flask app.

.. code-block:: guess

   ---
   hosts: localhost

   - name: install nginx
     yum: name=nginx state=installed

   - name: install pip
     yum: name=python-pip state=installed

   - name: install flask
     pip: name=flask

   - name: fetch application
     git: repo=https://gist.github.com/c454e2e839fcb20605a3.git dest=flask-demo

Now we should also copy the config file for Nginx and systemd service file for our flask app. We will also define a couple of handlers. Handlers are executed if there is any change in state of the task which is supposed to notifies them.

When we will be done with the workshop, our final playbook will look something like this:

.. code-block:: guess

   ---
   - hosts: localhost
     remote_user: fedora
     become: yes
     become_method: sudo
     vars:
       - server_port: 8080

     tasks:
       - name: install nginx
         yum: name=nginx state=installed

       - name: serve nginx config
         template: src=../files/flask.conf dest=/etc/nginx/conf.d/
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

       - name: set selinux to permissive for demo
         selinux: policy=targeted state=permissive

       handlers:
       - name: restart nginx
         service: name=nginx state=restarted

       - name: restart flask app
         service: name=flask-demo state=restarted

We can also skip a particular task or make a task execute only if a condition is met using the When statement.

.. code-block:: guess

    tasks:
      - shell: yum provides */elinks
        when: ansible_os_family == "RedHat"

Suppose we have a list of items we have to iterate on for a particular task, we can use loops like the following

.. code-block:: guess

    - name: add ssh users
      user:
        name: "{{ item }}"
        state: present
        generate_ssh_key: yes
      with_items:
         - sshuser1
         - sshuser2
         - sshuser3

We can also run certain tasks from a playbook by tagging them -

.. code-block:: guess

    ---
    - hosts: localhost
      become: yes
    
      tasks:
      - name: install nginx
        yum: name=nginx state=present
        tags:
          - system
    
      - name: install pip
        yum: name=python-pip state=present
        tags:
          - system
      
      - name: install flask
        pip: name=flask
        tags:
          - dev

We can run the system tagged tasks by running `ansible-playbook playbook.yml --ask-become-pass --tags system`

We can skip the system tagges tasks by running `ansible-playbook playbook.yml --ask-become-pass --skip-tags system`
