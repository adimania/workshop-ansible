Cloud Infra Provising
=====================

Ansible provide lots of module for different Cloud operators like AWS,
Openstack, Rackspace, digitalOcean ...etc. to manage your cloud infra.

http://docs.ansible.com/ansible/list_of_cloud_modules.html

Here we have sample playbook for openstack cloud provider.

vars/main.yml

::

    ---

    OS_USERNAME: user1
    OS_PASSWORD: demo_password
    OS_TENANT_NAME: user1
    OS_AUTH_URL: http://172.29.236.7:35357/v2.0
    KEY_NAME: controller-key
    SHARED_NETWORK: 11d0eb17-7e18-4a7b-978d-d9475c64d0e0
    FLAVOR: m1.tiny
    OSIMG: cirros-0.3.3
    INSTCNT: 3
    INSTNAME: ansible-demo


tasks/main.yml

::

    ---

    - name: Launch instances in tenant
      command: nova --os-username={{ OS_USERNAME }} --os-password={{ OS_PASSWORD }} --os-tenant-name={{ OS_TENANT_NAME }}
              --os-auth-url={{ OS_AUTH_URL }} boot --flavor {{ FLAVOR }} --image {{ OSIMG }} --nic net-id={{ SHARED_NETWORK }}
              --security-group default --key-name {{ KEY_NAME }} --min-count {{ INSTCNT }} {{ INSTNAME }}

you can use openstack-API instead of CLI to perform same task.


For DigitalOcean Droplet provisioning, refer to the respective directory in the root of this repository for playbooks.

Before running the playbooks, make sure you have done the following -

- `pip install dopy`
- Login to your DO account, and under API, generate your API token, and then export it to the environment as `DO_API_TOKEN=<token>`
