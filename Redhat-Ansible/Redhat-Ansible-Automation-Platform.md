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

