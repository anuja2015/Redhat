1. Clone the https://git.lab.example.com/student/develop-review.git Git repository into the /home/student/git-repos directory and then create a new branch named exercise.

![image](https://github.com/anuja2015/Redhat/assets/16287330/86ca2a62-fdf0-4d17-91d3-a2b6db2e021b)

![image](https://github.com/anuja2015/Redhat/assets/16287330/5a252806-7a11-4217-b75d-33831d260af3)

   
2. Ensure that plays and tasks have names associated with them. Add a name to the play in the site.yml playbook and add names to  the two tasks in the roles/test/tasks/main.yml file.

![image](https://github.com/anuja2015/Redhat/assets/16287330/beec2325-dcf4-47c1-94f3-0ce6a69f8269)

3. The site.yml playbook uses the test role to deploy the configuration changes. This role does not have a suitable name. Rename this role to grub and then update the site.yml playbook accordingly.

![image](https://github.com/anuja2015/Redhat/assets/16287330/1171dd67-1723-4cd6-a432-c54a77d6d5fd)
 
4. Change the two role variables names (timeout and persistent) to use the grub_ prefix. Update the roles/grub/tasks/main.yml and group_vars/lb_servers.yml files to use the new variable names. Although not evaluated, you might update the roles/grub/README.md file to reflect changes made in this exercise.

![image](https://github.com/anuja2015/Redhat/assets/16287330/ab98ef27-659a-4214-a71d-4f0cf22a946e)


![image](https://github.com/anuja2015/Redhat/assets/16287330/21639913-c830-41b7-ba40-1c9df5be1f92)


![image](https://github.com/anuja2015/Redhat/assets/16287330/8778ca63-84d1-43e8-b3bf-7b76d308e7f8)


  
5. Test the ~/git-repos/develop-review/site.yml playbook. Using the ee-supported-rhel8 execution environment, verify that the site.yml file runs without any errors. Automation execution environments are available from hub.lab.example.com by using student as the username and redhat123 as the password.

![image](https://github.com/anuja2015/Redhat/assets/16287330/54a01099-ef3a-478b-9079-48a8ad347fa6)

6. Push all of your changes to the exercise branch of the remote Git repository.

