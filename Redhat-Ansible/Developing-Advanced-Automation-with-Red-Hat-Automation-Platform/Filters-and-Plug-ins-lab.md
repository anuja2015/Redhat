# Lab: Transforming Data with Filters and Plug-ins

## Instructions

1. Clone the https://git.lab.example.com/student/data-review.git repository to the /home/student/git-repos directory and then create the exercise branch.

2. Examine the firewall role in the ~/git-repos/data-review project directory. The tasks file, roles/firewall/tasks/main.yml, contains three tasks that use the firewalld module to configure firewall rules defined by the firewall_rules variable. Edit the tasks file so that it uses filters to set default values for variables in each of the three tasks if they are not set, as follows:
• For the state option, if item['state'] is not set, then set it to enabled by default.
• For the zone option, if item['zone'] is not set, then omit the zone option.
• In the "Ensure Firewall Port Configuration" task, in the port option to the firewalld module, if item['protocol'] is not set then set it to tcp. Also use the lower filter to ensure that the value of the item['protocol'] option is in lowercase.

3. Test the changes you made to the roles/firewall/tasks/main.yml file in the preceding step by running the test_firewall_role.yml playbook. If you completed the preceding step successfully, the playbook runs without errors.

4. Examine the deploy_apache.yml playbook. It calls the apache role to ensure that Apache HTTP Server is deployed, which itself calls the firewall role. The playbook also defines the firewall_rules variable to make sure that the http service for firewalld and the IPv4 address of the load balancer (172.25.250.10) are both enabled in the internal zone for firewalld.
Edit the playbook. You need to change the value of the firewall_rules variable in the deploy_apache.yml playbook to a Jinja2 expression that uses the template lookup plug-in to dynamically generate the variable's setting from the apache_firewall_rules.yml.j2 Jinja2 template. You must use the from_yaml filter in the Jinja2 expression to convert the resulting value from a text string into a YAML data structure that can be interpreted by Ansible.

5. Examine the templates/apache_firewall_rules.yml.j2 template that your playbook now uses to set the firewall_rules variable.
For the first rule, the apache_port variable is set by files in the group_vars directory. The template contains a Jinja2 for loop that creates a rule for each host in the lb_servers group, setting the source IP address from the value of the load_balancer_ip_addr variable.
This is not the best solution. It requires you to set load_balancer_ip_addr as a host variable for each load balancer in the lb_servers group. To remove this manual maintenance, use gathered facts from these hosts to set that value instead. Edit the templates/apache_firewall_rules.yml.j2 template to replace the load_balancer_ip_addr host variable in the Jinja2 for loop with the
hostvars[server]['ansible_facts']['default_ipv4']['address'] fact.

6. Run the site.yml playbook to test your changes. If you successfully completed the preceding steps, then the playbook runs without errors.

7. Verify that web browser requests from workstation to the load balancer on servera succeed, and that direct requests from workstation to either TCP port 80 or TCP port 8008 on the back-end web servers, serverb and serverc, are denied.

8. Save your work, and then use Git to commit your changes and push them to the remote Git
repository. If prompted, use Student@123 as the Git password.
