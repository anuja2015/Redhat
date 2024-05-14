1. Clone the https://git.lab.example.com/student/inventory-review.git Git repository into the /home/student/git-repos directory and then create the exercise
branch. In the ~/git-repos/inventory-review/ directory, review the inventory file and then run the site.yml playbook using automation content navigator. You can use the curl command to verify that the same version of the web application is deployed to both back-end web servers by making at least two web requests to servera.

2. Configure the web servers in each host group to report different version numbers for the web application, as follows:
   Create a directory for variable files for the a_web_servers host group. Create a variable file in that directory called webapp.yml. That file must set the value of the webapp_version variable to v1.1a.
   Create another directory for the b_web_servers host group. It should also contain a variable file called webapp.yml. That second variable file must set the value of the webapp_version variable to v1.1b.

3. Using automation content navigator, run the deploy_webapp.yml playbook to update the version information displayed by the web application. Use the curl command to confirm that requests for web pages sent to servera produce two different versions of the web application.
