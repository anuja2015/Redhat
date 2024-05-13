# Lab:1 Developing Playbooks with Ansible Automation Platform

Remote Git Repository: https://git.lab.example.com/student/develop-review.git.

Instructions

1. Clone the https://git.lab.example.com/student/develop-review.git Git repository into the /home/student/git-repos directory and then create a new branch named exercise.
   
2. Ensure that plays and tasks have names associated with them. Add a name to the play in the site.yml playbook and add names to  the two tasks in the roles/test/tasks/main.yml file.
   
3. The site.yml playbook uses the test role to deploy the configuration changes. This role does not have a suitable name. Rename this role to grub and then update the site.yml playbook accordingly.
   
4. Change the two role variables names (timeout and persistent) to use the grub_ prefix. Update the roles/grub/tasks/main.yml and group_vars/lb_servers.yml files to use the new variable names. Although not evaluated, you might update the roles/grub/README.md file to reflect changes made in this exercise.
   
5. Test the ~/git-repos/develop-review/site.yml playbook. Using the ee-supported-rhel8 execution environment, verify that the site.yml file runs without any errors. Automation execution environments are available from hub.lab.example.com by using student as the username and redhat123 as the password.

6. Push all of your changes to the exercise branch of the remote Git repository.
