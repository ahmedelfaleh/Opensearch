# Opensearch Version Upgrade

This repository is intended to be created to automate upgrading OpenSearch version by Ansible playbook

## What this Ansible playbook do?

Please refer to <https://github.com/ahmedelfaleh/Opensearch/edit/main/version_upgrading.md>

## How to use?

1. Install ansible [core 2.13.7] on your control plane host + python 3.10.6 and install the same python on the remote servers
2. Allow internet connection on your remote servers to be able to download the new version packages
3. Set the environment variables that matches your current OpenSearch variables
   - main: /path/to/OpenSearch/group_vars/all.yml

     CRNT_OS_CONF_PATH: "" #The current opensearch config path

     OLD_OS_VERSION: "" #The current opensearch version

     NEW_OS_VERSION: "" #Change to the version you want to upgrade to

     OS_USER:

     DASHBOARD_CONF_PATH: ""

   - roles/opensearchUpgrade/vars/main.yml:

     OS_URL: "" #Change to master01 hostname

     OS_PORT: ""

     OS_USERNAME: ""

     OS_PASSWORD: '' #change to the correct admin password
4. Fill inventory/hosts with your hosts:

   [masters]

   name ansible_host=[IP or hostname] ansible_user=[ansible_username] ansible_ssh_private_key_file=[id_rsa location]

 And so on for every server and group

6. Run the playbook corresponding the targeted environment:
   - ansible-playbook -i inventory/non-prod opensearch.yml
