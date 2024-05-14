1. Clone the https://git.lab.example.com/student/inventory-review.git Git repository into the /home/student/git-repos directory and then create the exercise
branch. In the ~/git-repos/inventory-review/ directory, review the inventory file and then run the site.yml playbook using automation content navigator. You can use the curl command to verify that the same version of the web application is deployed to both back-end web servers by making at least two web requests to servera.

![image](https://github.com/anuja2015/Redhat/assets/16287330/2f22d1d1-9d05-4d70-b5c4-a6a6d3387594)

![image](https://github.com/anuja2015/Redhat/assets/16287330/757ce4c6-ac10-497b-aa76-b6ca3f5778de)

2. Configure the web servers in each host group to report different version numbers for the web application, as follows:
   Create a directory for variable files for the a_web_servers host group. Create a variable file in that directory called webapp.yml. That file must set the value of the webapp_version variable to v1.1a.
   Create another directory for the b_web_servers host group. It should also contain a variable file called webapp.yml. That second variable file must set the value of the webapp_version variable to v1.1b.

![image](https://github.com/anuja2015/Redhat/assets/16287330/8e02f27e-6f3f-465c-982f-ab6051fbf02b)

3. Using automation content navigator, run the deploy_webapp.yml playbook to update the version information displayed by the web application. Use the curl command to confirm that requests for web pages sent to servera produce two different versions of the web application.
Commit the files that you have created to your local Git repository.

![image](https://github.com/anuja2015/Redhat/assets/16287330/7f262ec0-7ad5-40a5-98ec-2db7b0b0feb3)

![image](https://github.com/anuja2015/Redhat/assets/16287330/19da6612-e326-4752-8418-566d45823e4e)

![image](https://github.com/anuja2015/Redhat/assets/16287330/91e3480f-75e7-4175-a3d4-c7f0de44a25e)


4. Create a YAML-formatted inventory file called inventory.yml using the data from the INI-formatted inventory file. If you generate the inventory.yml file using the ansible-navigator command, then remove the variables that are added for each host. Do not remove the original inventory file.
Run the site.yml playbook using the new inventory.yml file.

![image](https://github.com/anuja2015/Redhat/assets/16287330/00c0f6a0-913e-45ed-b890-f984a25f4cc0)

![image](https://github.com/anuja2015/Redhat/assets/16287330/f4b1e444-f39b-4be7-8cb3-4dc43c7a8a2e)

5. You have decided to change your YAML inventory to use inventory hostnames that are mapped to their purposes, rather than using actual hostnames. Modify the inventory.yml file as follows:
- In the lb_servers host group, change servera.lab.example.com to loadbalancer_1. Assign loadbalancer_1 an ansible_host variable that configures its real hostname as servera.lab.example.com.
- In the a_web_servers host group, change serverb.lab.example.com to backend_a1. Assign backend_a1 an ansible_host variable that configures its real hostname as serverb.lab.example.com.
- In the b_web_servers host group, change serverc.lab.example.com to backend_b1. Assign backend_b1 an ansible_host variable that configures its real hostname as serverc.lab.example.com.

![image](https://github.com/anuja2015/Redhat/assets/16287330/f58b093d-714f-433b-8773-d9234ee8ccad)


6. Verify that the site.yml playbook runs without errors when you use the updated inventory.yml inventory file. You can use the curl command to test the load balancer again.

![image](https://github.com/anuja2015/Redhat/assets/16287330/c8681aa7-9ac9-46c2-a49b-8b6f612969bf)

![image](https://github.com/anuja2015/Redhat/assets/16287330/deebbad1-b5d5-4fd0-8f8e-0921da7c33fd)


After the playbook runs without errors, commit the new inventory.yml file to your local Git repository. If prompted, then use Student@123 as the Git password. After you have committed all project changes, push the local commits to the remote repository.

![image](https://github.com/anuja2015/Redhat/assets/16287330/a550806c-b571-488b-8897-325c53ebb997)
