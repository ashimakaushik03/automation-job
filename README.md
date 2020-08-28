```
# automation-job repository

SUMMARY OF THE REPOSITORY:

Repository for creating EC2 Instance in AWS and installing Apache server over it using Ansible. The repo will first lunch the EC2 instance and then it will do ssh into the instance and then install apache web server onto it. It then tests and validates the installation of the apache web server to make sure that it is installed and running, and it also checks for the port it is listening on. The whole process is automated.

Below is the directory structure:
.
├── README.md
├── ansible.cfg
├── aws_keys
├── hosts
├── main.yml
├── roles
│   └── automation
│       ├── tasks
│       │   ├── apache_config_changes.yml
│       │   ├── apache_service_validation.yml
│       │   └── install_apache_service.yml
│       └── vars
└── vars.yml

STEPS TO RUN THE PLAYBOOK:

- First you need to export two environment variables AWS_ACCESS_KEY and SECRET_ACCESS_KEY. You should use your own AWS account user keys. 
- Then you need to create a new keypair in the region where you want to craete the EC2 machine (if you already have a keypair, you can use the existing one also). Then you will add this keypair file name in the vars.yml file (without the .pem or ppk extension).

- After completing the above steps you can execute the following command:

$ ansible-playbook main.yml

- The above command will give the output of the play which will launch an ec2 instance, ssh into it, installs python and apache2 server and tests/validates the configuration.

To MAKE THE CONFIGURATION CHANGES IN THE APACHE SERVER:

- There is a role which will do 2 configuration changes in the Apache server config file (It will change the port that apache server listens to and also it will change the LogLevel).

- To run this playbook, you can execute the below commands:

$ansible-playbook apache_config_changes.yml -i /Users/ashima/automation-job/hosts
