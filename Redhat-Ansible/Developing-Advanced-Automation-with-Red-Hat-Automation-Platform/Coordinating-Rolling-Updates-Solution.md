1. Clone the https://git.lab.example.com/student/update-review.git repository into the /home/student/git-repos/update-review directory, and then create the exercise branch for this exercise. Run the site.yml playbook to deploy the web application infrastructure.

![image](https://github.com/anuja2015/Redhat/assets/16287330/6e4fe35f-d262-4bca-9d3e-26a7304a9974)

![image](https://github.com/anuja2015/Redhat/assets/16287330/524d5106-5a38-4235-a6d2-38a917f535be)

![image](https://github.com/anuja2015/Redhat/assets/16287330/7f59a484-0df1-4127-8a69-97a41ad17adf)

![image](https://github.com/anuja2015/Redhat/assets/16287330/114888a6-2a85-4102-aa95-4f29eff1d025)

![image](https://github.com/anuja2015/Redhat/assets/16287330/c0fe3106-edda-4081-aab2-7700f81fff9d)

![image](https://github.com/anuja2015/Redhat/assets/16287330/5feae089-a52d-4d93-a448-a89b054e4558)

2. The update_webapp.yml playbook requires collections that are defined in the collections/requirements.yml file. Obtain a token from https://hub.lab.example.com by logging in as the student user with the redhat123 password. Use this token to update the token option in the ansible.cfg file. Use the ansible-galaxy command to install the collections. The collections must be available to the execution environment, so they must be installed in the /home/student/git-repos/update-review/collections/ directory.

![image](https://github.com/anuja2015/Redhat/assets/16287330/134a4e48-9965-44cb-8db4-85fb613b4fe5)

![image](https://github.com/anuja2015/Redhat/assets/16287330/31b0967c-f437-4d37-93cf-c91a17a0087d)

![image](https://github.com/anuja2015/Redhat/assets/16287330/8720b2e3-eff7-4b5a-8318-c412c8ee7da6)

![image](https://github.com/anuja2015/Redhat/assets/16287330/374f477a-0acc-4dc5-bcc6-528501da282c)

3. Add a pre_tasks section to the play in the update_webapp.yml playbook. Add a task to the section that disables the web servers on the HAProxy load balancer. Without this task, external clients might experience problems with the web application due to unforeseen deployment issues.
Configure the new task as follows:
- Use the community.general.haproxy module.
- Disable the host in the app back end by using the inventory_hostname variable.
- Delegate each action to the load balancer. The {{ groups['lb_servers'][0] }} Jinja2 expression provides the name of this load balancer.

![image](https://github.com/anuja2015/Redhat/assets/16287330/d3b76358-651f-4b49-9f76-b10a466921d1)

4. In the update_webapp.yml playbook, the first task in the post_tasks section is a "smoke test". That task verifies that the web application on each web server responds to requests that originate from that same server. This test is not realistic because requests to the web server normally originate from the load balancer, but it verifies that the web servers are
operating.
However, if you only test a web server's response from the web server itself, you do not test any network-related functions.
Using delegation, modify the smoke test task so that each request to a web server originates from the load balancer. Use the inventory_hostname variable to connect to each web server.

![image](https://github.com/anuja2015/Redhat/assets/16287330/5e481802-ab94-4407-8549-ab2a7a26f120)

5. Add a task to the post_tasks section after the smoke test to re-enable each web server on the HAProxy load balancer. This task is similar in structure to the community.general.haproxy task in the pre_tasks section, except that it sets the state to enabled instead of disabled.

![image](https://github.com/anuja2015/Redhat/assets/16287330/afbf4fb0-cfda-47e1-a3c7-e176632aca57)

6. Configure the play in the update_webapp.yml playbook to run through its tasks in batches to mitigate the effects of unforeseen deployment errors. Ensure that the playbook uses no more than three batches to complete the upgrade of all web server hosts. Set the first batch to consist of 5% of the hosts, the second batch 35% of the hosts, and the last batch to consist of all remaining hosts.
Add an appropriate keyword to the play to ensure that playbook execution stops if any host fails a task during the upgrade.

![image](https://github.com/anuja2015/Redhat/assets/16287330/331d8501-ec69-400d-a710-e87bc7ce75e7)

7. Run the update_webapp.yml playbook to perform the rolling update.
![image](https://github.com/anuja2015/Redhat/assets/16287330/b3d249cd-b644-4a0e-a4f3-2a0cb41f368f)
   
8. Commit and push your changes to the remote Git repository.

![image](https://github.com/anuja2015/Redhat/assets/16287330/a0a4fdcd-1ebb-46cd-baf7-68c8a90a8699)

