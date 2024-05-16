# Lab: Coordinating Rolling Updates

## Instructions
1. Clone the https://git.lab.example.com/student/update-review.git repository into the /home/student/git-repos/update-review directory, and then create the exercise branch for this exercise. Run the site.yml playbook to deploy the web application infrastructure.

2. The update_webapp.yml playbook requires collections that are defined in the collections/requirements.yml file. Obtain a token from https://hub.lab.example.com by logging in as the student user with the redhat123 password. Use this token to update the token option in the ansible.cfg file. Use the ansible-galaxy command to install the collections. The collections must be available to the execution environment, so they must be installed in the /home/student/git-repos/update-review/collections/ directory.

3. Add a pre_tasks section to the play in the update_webapp.yml playbook. Add a task to the section that disables the web servers on the HAProxy load balancer. Without this task, external clients might experience problems with the web application due to unforeseen deployment issues.
Configure the new task as follows:
- Use the community.general.haproxy module.
- Disable the host in the app back end by using the inventory_hostname variable.
- Delegate each action to the load balancer. The {{ groups['lb_servers'][0] }} Jinja2 expression provides the name of this load balancer.

4. In the update_webapp.yml playbook, the first task in the post_tasks section is a "smoke test". That task verifies that the web application on each web server responds to requests that originate from that same server. This test is not realistic because requests to the web server normally originate from the load balancer, but it verifies that the web servers are
operating.
However, if you only test a web server's response from the web server itself, you do not test any network-related functions.
Using delegation, modify the smoke test task so that each request to a web server originates from the load balancer. Use the inventory_hostname variable to connect to each web server.

5. Add a task to the post_tasks section after the smoke test to re-enable each web server on the HAProxy load balancer. This task is similar in structure to the community.general.haproxy task in the pre_tasks section, except that it sets the state to enabled instead of disabled.

6. Configure the play in the update_webapp.yml playbook to run through its tasks in batches to mitigate the effects of unforeseen deployment errors. Ensure that the playbook uses no more than three batches to complete the upgrade of all web server hosts. Set the first batch to consist of 5% of the hosts, the second batch 35% of the hosts, and the last batch to consist of all remaining hosts.
Add an appropriate keyword to the play to ensure that playbook execution stops if any host fails a task during the upgrade.

7. Run the update_webapp.yml playbook to perform the rolling update.
   
8. Commit and push your changes to the remote Git repository.
