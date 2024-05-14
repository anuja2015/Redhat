# Lab: Working with Ansible Configuration Settings

## Instructions

1. Change to the /home/student/config-review directory for your Ansible project and configure the automation content navigator settings file to use the hub.lab.example.com/ee-supported-rhel8:latest image by default, and set the pull policy to missing.

2. Because the install-web.yml playbook requires prompting for the privilege escalation password, you must disable creating playbook artifacts. Configure the automation content navigator settings file to disable creating playbook artifacts.

3. Use automation content navigator to determine how to specify the maximum number of forks Ansible uses to execute tasks on target hosts. Identify the name of the variable and to which section the variable belongs. Modify the ~/config-review/ansible.cfg Ansible configuration file to set the maximum number of forks to 15. Use automation content navigator to verify the changes.

4. Use the ansible-navigator command with the -m stdout and --ask-become-pass options to run the install-web.yml playbook. When prompted, enter student for the privilege escalation password. Verify that the playbook runs successfully.
