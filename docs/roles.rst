Roles
=========

Ansible playbooks can get very, very long with time, and hence difficult to maintain. Also, if you would like to reuse a subset of tasks from a playbook, that would get difficult as the playbooks get bigger and bigger.

Ansible roles can help you with grouping content, managing playbooks for a large project.

Example project structure::

    site.yml
    webservers.yml
    fooservers.yml
    roles/
       common/
         files/
         templates/
         tasks/
         handlers/
         vars/
         defaults/
         meta/
       webservers/
         files/
         templates/
         tasks/
         handlers/
         vars/
         defaults/
         meta/

In a playbook, it would look like this::

    ---
    - hosts: webservers
      roles:
         - common
         - webservers


This designates the following behaviors, for each role 'x':

- If roles/x/tasks/main.yml exists, tasks listed therein will be added to the play
- If roles/x/handlers/main.yml exists, handlers listed therein will be added to the play
- If roles/x/vars/main.yml exists, variables listed therein will be added to the play
- If roles/x/defaults/main.yml exists, variables listed therein will be added to the play
- If roles/x/meta/main.yml exists, any role dependencies listed therein will be added to the list of roles (1.3 and later)
- Any copy, script, template or include tasks (in the role) can reference files in roles/x/{files,templates,tasks}/ (dir depends on task) without having to path them relatively or absolutely
