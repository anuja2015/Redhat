# Red Hat Ansible Automation Platform 2 Components

- Ansible-Core
- Ansible content Collections
- Automation Content Navigator
- Automation Execution Environments
- Automation Controller
- Automation Hub

### Ansible Core

- defines the automation language that is used to write Ansible Playbooks in YAML text files.
- provides the key functions such as loops, conditionals, and other Ansible imperatives needed for automation code.
- ansible.builtin Ansible Content Collection is always part of Ansible Core

### Ansible Content Collections

- made up of related modules, roles, and plug-ins that are supported by the same group of developers.

### Automation Content Navigator

- replaces and extends the functionality of several earlier command-line utilities, including ansible-playbook, ansible inventory, and ansible-config.
- run playbooks in a container.
- separates the control node, on which you run Ansible, from the automation execution environment that runs it.

### Automation Execution Environments

- a container image that contains Ansible Core, Ansible Content Collections, and any Python libraries, executables, or other dependencies needed to run the playbook.

### Automation Controller

- earlier called as Red Hat Ansible Tower
- The component of Ansible Automation Platform that provides a central point of control to run the enterprise automation code.
- It provides a web UI and a REST API that can be used to configure, run, and evaluate your automation jobs

### Automation Hub

- public service at console.redhat.com provides access to Red Hat Ansible Certified Content Collections that can be downloaded and used with ansible-galaxy (for ansible-navigator) and with automation controller.
- private automation hub enables  to create our own curated set of Ansible Content Collections

## Install ansible-navigator

1. Register the system using Redhat subscription manager

       subscription-manager register
   
2. Enable RedHat Ansible Automation Platform 2

        subscription-manager repos --enable ansible-automation-platform-2.2-for-rhel-8-x86_64-rpm

3. Install ansible-navigator

       yum install ansible-navigator

## Automation execution environment

- When running ansible-navigator use __--execution-environment-image (--eei)__ option to select a specific container image to use as the automation execution
- By default ee-supported-rhel8:latest is the execution environment.
- __--pull-policy (--pp)__ option  controls how ansible-navigator pulls container images.
- When the value of --pp option is set to __missing__, automation content navigator only pulls the container image if the image does not exist on the local system.



