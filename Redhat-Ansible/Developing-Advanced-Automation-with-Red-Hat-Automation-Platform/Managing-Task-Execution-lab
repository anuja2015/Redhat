# Lab: Managing Task Execution

## Instructions

1. Clone the https://git.lab.example.com/student/task-review.git repository to the /home/student/git-repos directory and then create the exercise branch.

2. Modify the ansible.cfg file so that privilege escalation is disabled by default. Because all the tasks in the firewall, haproxy, apache, and webapp roles require privilege escalation, enable privilege escalation at the play level in the deploy_apache.yml, deploy_haproxy.yml, and deploy_webapp.yml playbooks.

3. In the deploy_haproxy.yml playbook, add a copy task that runs before any other task in the play. That task must write the text Playbook site.yml ready to start to the /tmp/site.ready file on the servers in the lb_servers group.

4. Add a handler to the haproxy role that writes the message Reloaded to the /tmp/haproxy.status file. Notify the handler if the task that uses the template module in the haproxy role reports that the state of the system changed. Use haproxy filehandler as the name of the handler.

5. Add the apache_installer tag to the yum task in the apache role.

6. Enable the timer and profile_tasks callback plug-ins for the playbook. The two plug-ins are part of the ansible.posix collection. If desired, then you can specify the FQCNs for the callback plug-ins.

7. Use automation content navigator to run the site.yml playbook in stdout mode. Analyze the output to find the task that uses the most time.

8. Refactor the most expensive task to make it more efficient. When done, run the cleanup_apache.yml playbook to clean up the web servers so that you can compare the results. To verify the changes, run the site.yml playbook with an appropriate tag so that you only run the modified task.

9. Commit and push your changes to the remote Git repository.
