This lab provides you with a Git repository that contains a working playbook to deploy a simple web server. Create all resources from the automation controller web UI located at https://controller.lab.example.com. Log in as the admin user with redhat as the password.

1. Create a source control credential named reviewgitcred. The credential must belong to the Default organization. The GitLab user for the credential is student. Use the private key stored in the /home/student/.ssh/gitlab_rsa file on the workstation machine
as the SCM private key.

![image](https://github.com/anuja2015/Redhat/assets/16287330/92f86661-9c53-4331-a876-c266c67c4503)

![image](https://github.com/anuja2015/Redhat/assets/16287330/0f242ead-3d2e-49a5-9e1d-7282f18b1dfd)

![image](https://github.com/anuja2015/Redhat/assets/16287330/b56364b9-2ec0-49d7-96a7-bf23b136e1b4)

![image](https://github.com/anuja2015/Redhat/assets/16287330/7491d251-53d8-480d-89cf-32871b944ac3)

2. Create a machine credential named reviewmachinecred. The credential must belong to the Default organization. Configure this credential for the devops user. Use the SSH private key stored in the /home/student/.ssh/lab_rsa file. Use sudo as the privilege escalation method and root as the privilege escalation username.

![image](https://github.com/anuja2015/Redhat/assets/16287330/ca792963-1f34-4444-8ae1-10bd3016ba11)

![image](https://github.com/anuja2015/Redhat/assets/16287330/dd5e3d1d-f6fb-456c-bd0c-f3ca3cbbb33d)

![image](https://github.com/anuja2015/Redhat/assets/16287330/11e211bc-80f0-4a39-a7b1-5751f4ee5f86)

3. Create an inventory named reviewinventory. The inventory must belong to the Default organization. Add the servera.lab.example.com host to this inventory.

![image](https://github.com/anuja2015/Redhat/assets/16287330/62038cf4-b175-4555-95a1-58f22ca3bb5f)

![image](https://github.com/anuja2015/Redhat/assets/16287330/387da5b0-1eff-423d-9e05-eac7406a100a)


4. Create a project named reviewproject. The project must belong to the Default organization. This project must use the git@git.lab.example.com:student/controller-review.git Git repository and use the reviewgitcred source control credential to authenticate to the repository.

![image](https://github.com/anuja2015/Redhat/assets/16287330/f0159b66-c0ad-45df-8854-c51e5fb9747d)

![image](https://github.com/anuja2015/Redhat/assets/16287330/8aca7b9b-4b82-43bd-9679-ee26e74e39e4)

![image](https://github.com/anuja2015/Redhat/assets/16287330/ecc6c1f8-b162-40d2-a992-94260bd2a113)


5. Create a job template named reviewtemplate. Configure the job template to use the reviewinventory inventory, the reviewproject project, the webserver.yml playbook, and the reviewmachinecred machine credential. Configure the job template to use the Automation Hub Default execution environment execution environment. Launch a job that uses the reviewtemplate job template. If you completed the exercise correctly, then navigating to http://servera.lab.example.com displays the following message:
			Successful playbook run from automation controller.

![image](https://github.com/anuja2015/Redhat/assets/16287330/3880571b-8d5e-4b88-8b3a-94e2ae917d12)

![image](https://github.com/anuja2015/Redhat/assets/16287330/f0a68157-1df0-44db-8ac9-72c754a7ccfb)

![image](https://github.com/anuja2015/Redhat/assets/16287330/826c9201-fa02-4d9a-a13c-585c1010dfa4)

![image](https://github.com/anuja2015/Redhat/assets/16287330/3001dcbd-19e8-4c07-9198-e30ca12893ba)

![image](https://github.com/anuja2015/Redhat/assets/16287330/c5f57064-4629-41e6-9e7b-6f465cb054ee)



