1. Change into the /home/student/manage-review/ directory and review the cockpit.yml playbook. Make note of the Ansible Content Collections that the playbook requires.

![image](https://github.com/anuja2015/Redhat/assets/16287330/66c54428-c7e5-4f83-abc4-f5f2318f37ae)

2. Use the ansible-navigator command to inspect the automation execution environment images available on your local system. Determine which one you need to run the cockpit.yml playbook.

        ansible-navigator images
   
![image](https://github.com/anuja2015/Redhat/assets/16287330/4fedd9bb-54ff-4e64-9fc5-06fb34780cec)

![image](https://github.com/anuja2015/Redhat/assets/16287330/38608865-2a35-42e1-99b2-947ae2a9f1de)

4. Run the cockpit.yml playbook by using the ansible-navigator command with the correct automation execution environment image.

![image](https://github.com/anuja2015/Redhat/assets/16287330/c4efaf42-2523-49c8-8778-1e8d346decd7)

5. Log in to the web console at https://servera.lab.example.com:9090 to confirm that the playbook correctly configured the web console. Accept the insecure TLS certificate and then log in as the student user. Use student as the password.

![image](https://github.com/anuja2015/Redhat/assets/16287330/4ff3ecdd-ec14-4cd9-9f1c-e7e4eecbca1f)

6. Review the create_samples_db.yml playbook. Make note of the collections that it requires. Find those collections in the private automation hub. You can access the private automation hub web UI at https://hub.lab.example.com. Use student as the username and redhat123 as the password.
![image](https://github.com/anuja2015/Redhat/assets/16287330/50bee8f5-5b77-4d78-878a-01d4d3eeb529)

![image](https://github.com/anuja2015/Redhat/assets/16287330/42d81d36-09d5-42f5-aeb4-a7827349ce78)

7. Configure the /home/student/manage-review/ansible.cfg file so that the ansible-galaxy command installs collections from private automation hub.

![image](https://github.com/anuja2015/Redhat/assets/16287330/0aad5894-6b41-4284-bc3f-b09254ba1d56)

8. Create the /home/student/manage-review/collections/ directory. In this directory, install any collections that the create_samples_db.yml playbook requires.

![image](https://github.com/anuja2015/Redhat/assets/16287330/f2728918-bc5d-47a9-a1d9-964d15bcba33)

![image](https://github.com/anuja2015/Redhat/assets/16287330/38a06ed5-0f08-4ce9-ae20-ee155a13ad4c)

9. Use the ansible-navigator command to run the create_samples_db.yml playbook.

![image](https://github.com/anuja2015/Redhat/assets/16287330/e504fc30-a1a5-4558-8e6e-cd8116509bd6)


10. Confirm that the playbook correctly configured a MariaDB database on the serverb machine. You can confirm that the playbook created the samples database by running the sudo mysql -e "SHOW DATABASES" command. The password for the student user is student.

![image](https://github.com/anuja2015/Redhat/assets/16287330/dc9e49fb-9984-4db1-9b18-f215506fd071)
