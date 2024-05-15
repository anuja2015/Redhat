1. Clone the https://git.lab.example.com/student/task-review.git repository to the /home/student/git-repos directory and then create the exercise branch.

![image](https://github.com/anuja2015/Redhat/assets/16287330/9239b37f-a350-489e-a9f3-54a493888d6d)

2. Modify the ansible.cfg file so that privilege escalation is disabled by default. Because all the tasks in the firewall, haproxy, apache, and webapp roles require privilege escalation, enable privilege escalation at the play level in the deploy_apache.yml, deploy_haproxy.yml, and deploy_webapp.yml playbooks.

![image](https://github.com/anuja2015/Redhat/assets/16287330/bdced076-ee0d-4e0c-ba67-7770a0fd48c7)

![image](https://github.com/anuja2015/Redhat/assets/16287330/2adbb10c-7894-43b0-968a-3086de7e8ef9)

3. In the deploy_haproxy.yml playbook, add a copy task that runs before any other task in the play. That task must write the text Playbook site.yml ready to start to the /tmp/site.ready file on the servers in the lb_servers group.

![image](https://github.com/anuja2015/Redhat/assets/16287330/15a4fe58-0b1b-4d62-ae6e-550820b4d29b)

4. Add a handler to the haproxy role that writes the message Reloaded to the /tmp/haproxy.status file. Notify the handler if the task that uses the template module in the haproxy role reports that the state of the system changed. Use haproxy filehandler as the name of the handler.

![image](https://github.com/anuja2015/Redhat/assets/16287330/47d92cfe-9a17-477e-a244-346dbe653a11)

![image](https://github.com/anuja2015/Redhat/assets/16287330/dbaa020a-cbf5-44eb-9814-91ad4e090e7d)

5. Add the apache_installer tag to the yum task in the apache role.

![image](https://github.com/anuja2015/Redhat/assets/16287330/b8fac583-575a-4fa9-819c-da6e7718e3a6)


6. Enable the timer and profile_tasks callback plug-ins for the playbook. The two plug-ins are part of the ansible.posix collection. If desired, then you can specify the FQCNs for the callback plug-ins.

![image](https://github.com/anuja2015/Redhat/assets/16287330/03f559d6-2ee6-4e57-bfbc-20474227f2ac)

7. Use automation content navigator to run the site.yml playbook in stdout mode. Analyze the output to find the task that uses the most time.

![image](https://github.com/anuja2015/Redhat/assets/16287330/a103a668-3f68-42af-aca4-342c209f12f9)

![image](https://github.com/anuja2015/Redhat/assets/16287330/30f998c4-86e2-4445-946b-a96b66e6f88d)


8. Refactor the most expensive task to make it more efficient. When done, run the cleanup_apache.yml playbook to clean up the web servers so that you can compare the results. To verify the changes, run the site.yml playbook with an appropriate tag so that you only run the modified task.

![image](https://github.com/anuja2015/Redhat/assets/16287330/0858397c-0150-4444-8b8f-48590552d43e)

![image](https://github.com/anuja2015/Redhat/assets/16287330/51adb775-3f9d-424f-b882-a7511c297432)

![image](https://github.com/anuja2015/Redhat/assets/16287330/aeff1677-b144-4dbd-a742-62364ad6d42b)


9. Commit and push your changes to the remote Git repository.

![image](https://github.com/anuja2015/Redhat/assets/16287330/19431ac2-ede1-4214-af04-4f17f156d5be)

![image](https://github.com/anuja2015/Redhat/assets/16287330/906390df-0f56-4495-812c-9fb038d8646f)

