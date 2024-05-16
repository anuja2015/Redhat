
1. On the workstation machine, in the /home/student/create-review directory, create an Ansible Content Collection named training.web that includes two roles and a lookup plug-in.
The two roles are available in the /home/student/create-review/roles/ directory. You have to copy them to the correct location in the collection after you create the skeleton directories for the collection.
The firewall role depends on the ansible.posix collection (version >=1.0.0). Configure your collection to specify this dependency.
The lookup plug-in creates a QR (Quick Response) code in PNG (Portable NetworkGraphics) format. It is available in the /home/student/create-review/lookup.tgz file. Extract that archive into the correct location in your collection. It also requires the
Pillow and qrcode Python packages. Configure your collection to specify those two Python dependencies.
The collection requires Ansible version 2.9.10 or later. Build the collection and then copy the resulting .tar.gz file to the /home/student/create-review/ directory.

![image](https://github.com/anuja2015/Redhat/assets/16287330/cae22af2-fb6d-47ad-a6a3-938d11157cf3)

![image](https://github.com/anuja2015/Redhat/assets/16287330/63a49a07-31f7-45ff-ab1f-04a6b46e0c7b)

![image](https://github.com/anuja2015/Redhat/assets/16287330/59f902b1-bb02-4f8b-b769-6ab85883d62c)

![image](https://github.com/anuja2015/Redhat/assets/16287330/59a8ed6f-5f6e-40b6-934f-6f62201f8a90)

![image](https://github.com/anuja2015/Redhat/assets/16287330/e96d8ff6-b1a6-4803-8855-ee34d7fd8321)

![image](https://github.com/anuja2015/Redhat/assets/16287330/d41564e1-4bb2-48a1-9284-1449610d3c8e)

![image](https://github.com/anuja2015/Redhat/assets/16287330/5238e49e-89bf-4c97-9132-d3df31b80bfd)


2. Publish the training.web collection to your private automation hub. Use the private automation hub web UI to create a collection namespace named training and configure the Content Developers group to be namespace owners of the collection.
Upload the training.web collection to that namespace, and approve the collection after you upload it.

![image](https://github.com/anuja2015/Redhat/assets/16287330/461c65db-5581-4820-951f-bffe933e3cd2)

![image](https://github.com/anuja2015/Redhat/assets/16287330/3d83f184-45b0-4a7f-875b-2840d6ec173c)

![image](https://github.com/anuja2015/Redhat/assets/16287330/830996c8-f585-4444-a515-68079a277c67)

![image](https://github.com/anuja2015/Redhat/assets/16287330/bc9f70c0-5e05-4116-96ce-136fc625a54c)

![image](https://github.com/anuja2015/Redhat/assets/16287330/18a6a895-b655-4c37-ba6b-f9aa41276ad4)

3. Install the ansible-builder package on the workstation machine. The student user can run commands with escalated privileges. Use student as the sudo password.

![image](https://github.com/anuja2015/Redhat/assets/16287330/766dac0e-a751-4659-b210-801391f89553)

4. Prepare the configuration files to build a custom automation execution environment so that the training.web collection is included in it.
- On workstation, create the ~/create-review/ee-build directory to store the configuration files.
- Create an ee-build/execution-environment.yml file to control the build process. An example file is available in the /home/student/create-review/ directory. If you use that example file, then you must remove the parameters that you do not need.
   i. Set the hub.lab.example.com/ee-minimal-rhel8:latest container image asthe base image.
  ii. Set the hub.lab.example.com/ansible-builder-rhel8:latest container image as the builder image.

  ![image](https://github.com/anuja2015/Redhat/assets/16287330/ab3b3c14-3f7a-493a-b66c-c1c090482804)


- Copy the ~/create-review/ansible.cfg file to the ~/create-review/ee-build/ directory. That file configures access to the private automation hub at https://hub.lab.example.com so that the build process can retrieve the training.web and the ansible.posix collections.
- Get a token from the private automation hub web UI, and edit that ansible.cfg file to update both token parameters. Use the same token from private automation hub for both parameters.

![image](https://github.com/anuja2015/Redhat/assets/16287330/4e1dd16d-dd5b-4d68-b01a-94e7ffae861e)

- Create the ee-build/requirements.yml file and configure it to install the training.web collection into the automation execution environment.

![image](https://github.com/anuja2015/Redhat/assets/16287330/e19fc07c-25a9-44f5-8e0e-846d8415330b)

5. Configure the container image to include your private automation hub's TLS CA certificate. In the ~/create-review/ee-build/ directory, use the ansible-builder command to create the ee-build/context/ directory by performing the first stage of the build
process. Add the lab environment's TLS CA certificate to the container image. This enables the build process to retrieve collections from the lab environment's private automation hub. You have been provided with two files to help you do this, which should be used as follows:
- Copy ~/create-review/Containerfile to ~/create-review/ee-build/context/Containerfile.
- Copy /etc/pki/tls/certs/classroom-ca.pem to ~/create-review/ee-build/context/classroom-ca.pem.

![image](https://github.com/anuja2015/Redhat/assets/16287330/43ba6d32-f1f3-4534-8d9a-20248eeff65f)

![image](https://github.com/anuja2015/Redhat/assets/16287330/b40be552-31aa-4d54-9045-14b518e4dd85)

6. Build the automation execution environment container image and use hub.lab.example.com/review/ee-training-rhel8:v1.0 as the tag. Push the container image to the hub.lab.example.com container registry

7. Use the automation controller web UI to create an execution environment resource that uses the following settings:



8. Create an automation controller job template that uses the following settings:



9. Start a job that uses the Deploy QR Codes job template and verify that the job completes successfully. If successful, then navigating to http://serverf.lab.example.com displays a QR code image.
