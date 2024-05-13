1. Change into the /home/student/manage-review/ directory and review the cockpit.yml playbook. Make note of the Ansible Content Collections that the playbook requires.


2. Use the ansible-navigator command to inspect the automation execution environment images available on your local system. Determine which one you need to run the cockpit.yml playbook.

3. Run the cockpit.yml playbook by using the ansible-navigator command with the correct automation execution environment image.

4. Log in to the web console at https://servera.lab.example.com:9090 to confirm that the playbook correctly configured the web console. Accept the insecure TLS certificate and then log in as the student user. Use student as the password.

5. Review the create_samples_db.yml playbook. Make note of the collections that it requires. Find those collections in the private automation hub. You can access the private automation hub web UI at https://hub.lab.example.com. Use student as the username and redhat123 as the password.

6. Configure the /home/student/manage-review/ansible.cfg file so that the ansible-galaxy command installs collections from private automation hub.

7. Create the /home/student/manage-review/collections/ directory. In this directory, install any collections that the create_samples_db.yml playbook requires.

8. Use the ansible-navigator command to run the create_samples_db.yml playbook.

9. Confirm that the playbook correctly configured a MariaDB database on the serverb machine. You can confirm that the playbook created the samples database by running the sudo mysql -e "SHOW DATABASES" command. The password for the student user is student.
