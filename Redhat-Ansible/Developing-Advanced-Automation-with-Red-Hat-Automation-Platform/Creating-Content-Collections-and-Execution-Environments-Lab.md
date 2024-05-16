# Lab: Creating Content Collections and Execution Environments

## Instructions

1. On the workstation machine, in the /home/student/create-review directory, create an Ansible Content Collection named training.web that includes two roles and a lookup plug-in.
The two roles are available in the /home/student/create-review/roles/ directory. You have to copy them to the correct location in the collection after you create the skeleton directories for the collection.
The firewall role depends on the ansible.posix collection (version >=1.0.0). Configure your collection to specify this dependency.
The lookup plug-in creates a QR (Quick Response) code in PNG (Portable NetworkGraphics) format. It is available in the /home/student/create-review/lookup.tgz file. Extract that archive into the correct location in your collection. It also requires the
Pillow and qrcode Python packages. Configure your collection to specify those two Python dependencies.
The collection requires Ansible version 2.9.10 or later. Build the collection and then copy the resulting .tar.gz file to the /home/student/create-review/ directory.

2. Publish the training.web collection to your private automation hub. Use the private automation hub web UI to create a collection namespace named training and configure the Content Developers group to be namespace owners of the collection.
Upload the training.web collection to that namespace, and approve the collection after you upload it.

3. Install the ansible-builder package on the workstation machine. The student user can run commands with escalated privileges. Use student as the sudo password.

4. Prepare the configuration files to build a custom automation execution environment so that the training.web collection is included in it.
- On workstation, create the ~/create-review/ee-build directory to store the configuration files.
- Create an ee-build/execution-environment.yml file to control the build process. An example file is available in the /home/student/create-review/ directory. If you use that example file, then you must remove the parameters that you do not need.
   i. Set the hub.lab.example.com/ee-minimal-rhel8:latest container image asthe base image.
  ii. Set the hub.lab.example.com/ansible-builder-rhel8:latest container image as the builder image.
- Copy the ~/create-review/ansible.cfg file to the ~/create-review/ee-build/ directory. That file configures access to the private automation hub at https://hub.lab.example.com so that the build process can retrieve the training.web and the ansible.posix collections.
- Get a token from the private automation hub web UI, and edit that ansible.cfg file to update both token parameters. Use the same token from private automation hub for both parameters.
- Create the ee-build/requirements.yml file and configure it to install the training.web collection into the automation execution environment.

5. Configure the container image to include your private automation hub's TLS CA certificate. In the ~/create-review/ee-build/ directory, use the ansible-builder command to create the ee-build/context/ directory by performing the first stage of the build
process. Add the lab environment's TLS CA certificate to the container image. This enables the build process to retrieve collections from the lab environment's private automation hub. You have been provided with two files to help you do this, which should be used as follows:
- Copy ~/create-review/Containerfile to ~/create-review/ee-build/context/Containerfile.
- Copy /etc/pki/tls/certs/classroom-ca.pem to ~/create-review/ee-build/context/classroom-ca.pem.

6. Build the automation execution environment container image and use hub.lab.example.com/review/ee-training-rhel8:v1.0 as the tag. Push the container image to the hub.lab.example.com container registry

7. Use the automation controller web UI to create an execution environment resource that uses
the following settings:

![image](https://github.com/anuja2015/Redhat/assets/16287330/b9ad5876-29e2-47fc-bcd2-3d2f42d67601)

8. Create an automation controller job template that uses the following settings:

![image](https://github.com/anuja2015/Redhat/assets/16287330/4fc18c56-976e-4f0c-9e59-5d74e9f832ae)

9. Start a job that uses the Deploy QR Codes job template and verify that the job completes successfully. If successful, then navigating to http://serverf.lab.example.com displays a QR code image.
