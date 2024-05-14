# Lab: Running Playbooks with Automation Controller

This lab provides you with a Git repository that contains a working playbook to deploy a simple web server. Create all resources from the automation controller web UI located at https://controller.lab.example.com. Log in as the admin user with redhat as the password.

1. Create a source control credential named reviewgitcred. The credential must belong to the Default organization. The GitLab user for the credential is student. Use the private key stored in the /home/student/.ssh/gitlab_rsa file on the workstation machine
as the SCM private key.

2. Create a machine credential named reviewmachinecred. The credential must belong to the Default organization. Configure this credential for the devops user. Use the SSH private key stored in the /home/student/.ssh/lab_rsa file. Use sudo as the privilege escalation method and root as the privilege escalation username.

3. Create an inventory named reviewinventory. The inventory must belong to the Default organization. Add the servera.lab.example.com host to this inventory.

4. Create a project named reviewproject. The project must belong to the Default organization. This project must use the git@git.lab.example.com:student/controller-review.git Git repository and use the reviewgitcred source control credential to authenticate to the repository.

5. Create a job template named reviewtemplate. Configure the job template to use the reviewinventory inventory, the reviewproject project, the webserver.yml playbook, and the reviewmachinecred machine credential. Configure the job template to use the Automation Hub Default execution environment execution environment. Launch a job that uses the reviewtemplate job template. If you completed the exercise correctly, then navigating to http://servera.lab.example.com displays the following message:

             Successful playbook run from automation controller.
