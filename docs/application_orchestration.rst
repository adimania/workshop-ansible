Application Orchestration
=========================

Ansible can be used to deploy applications. A very obvious strategy is to package the application into rpm or deb package and use yum or apt module of ansible to install the application. Handlers can be used to reload or restart the application post the deploy. Alternatively, git module can be used to clone or pull the code from a repository and install or update the application.

Example:

.. code-block:: none

  - name: fetch application
    git: repo=https://gist.github.com/c454e2e839fcb20605a3.git dest=/opt/flask-demo
