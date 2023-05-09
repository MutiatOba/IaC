### What is infrastructure as Code (IaC)

Infrastructure as code (IaC) enables you to use code to automate the provisioning and management of infrastructure resources, such as virtual machines, networks, storage, and other components of an IT environment.

IaC tools, such as Terraform, CloudFormation, Ansible, and Puppet, can use the code or configuration files to create, configure, and manage infrastructure resources. IaC allows for the automated provisioning of infrastructure in a consistent and repeatable way, which can reduce errors and increase efficiency in managing infrastructure at scale.

### Benefits of IaC

1. Consistency and repeatability: IaC allows for the automated provisioning and configuration of infrastructure resources in a consistent and repeatable way. This can reduce the likelihood of errors and ensure that infrastructure is set up correctly every time.

2. Scalability: IaC can easily scale up or down depending on the demand. With IaC, infrastructure resources can be quickly created, modified, and deleted to meet the changing needs of an application or business.

3. Speed and agility: IaC can significantly reduce the time required to provision and configure infrastructure. With IaC, teams can quickly and easily create new infrastructure environments or make changes to existing ones.

4. Cost savings: IaC can help organizations save money by reducing the amount of time and effort required to manage infrastructure manually. This can free up resources for other important tasks.

5. Collaboration and version control: IaC allows for infrastructure definitions to be version-controlled and stored in a source code repository, enabling teams to collaborate, review, and manage changes to infrastructure in the same way they do with application code.

6. Compliance and security: IaC can help ensure that infrastructure resources are provisioned and configured in a compliant and secure manner. IaC can also help ensure that infrastructure resources are consistent with security policies and standards.

### Use cases for IaC

1. Provisioning and managing cloud resources: IaC can be used to create and manage cloud resources, such as virtual machines, databases, load balancers, and networking components. This enables teams to automate the provisioning and management of cloud infrastructure, making it easier to scale applications and services.

2. Deploying applications: IaC can be used to deploy applications to different environments, such as development, testing, and production. This enables teams to automate the deployment process and reduce errors caused by manual deployments.

3. Disaster recovery: IaC can be used to automate the disaster recovery process, enabling teams to quickly and easily restore infrastructure in the event of a disaster.

4. Compliance and security: IaC can be used to ensure that infrastructure resources are provisioned and configured in a compliant and secure manner. This can help organizations meet regulatory requirements and reduce the risk of security breaches.

5. Testing and validation: IaC can be used to create and manage test environments, enabling teams to test and validate infrastructure changes before deploying them to production.

6. Continuous integration and delivery: IaC can be used to automate the continuous integration and delivery process, enabling teams to deliver code changes to production more quickly and with greater reliability.

The following companies use IaC:

1. Amazon: Amazon uses IaC extensively to manage their cloud infrastructure on AWS. They have developed their own IaC tool called CloudFormation, which allows users to define and deploy AWS resources using templates.

2. Netflix: Netflix uses IaC to manage their cloud infrastructure on AWS. They use a combination of tools such as Spinnaker, Asgard, and Simian Army to automate the deployment and management of their infrastructure.

3. Airbnb: Airbnb uses IaC to manage their cloud infrastructure on AWS. They use a combination of tools such as Terraform and Ansible to automate the provisioning and configuration of their infrastructure.

4. Spotify: Spotify uses IaC to manage their cloud infrastructure on Google Cloud Platform (GCP). They use a combination of tools such as Terraform and Kubernetes to automate the deployment and management of their infrastructure.

### What is configuration management 

Configuration management aims to ensure that IT infrastructure is reliable, efficient, and secure by providing a consistent and standardised way to manage and track changes. This can help organisations to reduce the risk of downtime, improve system availability, and maintain compliance with regulatory requirements.

### What is ansible and its use cases

Ansible is a suite of software tools that enables infrastructure as code. It is open-source and the suite includes software provisioning, configuration management, and application deployment functionality.

Some of the key benefits of Ansible include:

1. Simple and easy to use: Ansible uses a simple, human-readable language called YAML, making it easy to read, write and understand.

2. Agentless architecture: Ansible does not require any agents to be installed on the target hosts, making it easy to manage and deploy resources across a wide range of platforms.

3. Scalable and flexible: Ansible can manage large-scale infrastructures and can be easily integrated with other automation tools and processes.

4. Secure: Ansible uses SSH for communication, which is secure by default, and supports encryption for sensitive data.

5. Community support: Ansible has a large and active community of users and contributors, which provides a wealth of resources and support.

Use cases for Ansible include:

1. Configuration management: Ansible can be used to automate the configuration and management of infrastructure resources, including servers, networks, and storage.

2. Application deployment: Ansible can automate the deployment of applications and services to a variety of platforms, including cloud-based environments.

3. Continuous delivery: Ansible can be integrated with other continuous delivery tools, such as Jenkins or GitLab, to automate the entire software delivery pipeline.

4. Disaster recovery: Ansible can be used to automate the recovery of infrastructure resources in the event of a disaster or outage.

5. Compliance and security: Ansible can be used to enforce security policies and compliance standards across the IT infrastructure.

YAML and playbook:

YAML stands for "YAML Ain't Markup Language" and it is a human-readable data serialization format that is often used for configuration files, data exchange, and other applications where human readability is desired. In Ansible, YAML is used for writing playbooks.

A playbook in Ansible is a set of instructions that describe the tasks to be performed by Ansible on a group of hosts. Playbooks are written in YAML and contain a series of tasks that are executed in sequence. Each task defines a set of actions to be performed on a specific host or group of hosts. Playbooks can be used to automate the deployment and management of infrastructure resources, as well as the configuration of applications and services.

### Steps to set up Ansible

Need a scrip to launch controller virtual machine.

Head over to visual studio code:
- cd to the relevant folder
- type vagrant init - which will create a vagrant file
- update the vagrant file:
```
# ansible-tech201


# -*- mode: ruby -*-
 # vi: set ft=ruby :
 
 # All Vagrant configuration is done below. The "2" in Vagrant.configure
 # configures the configuration version (we support older styles for
 # backwards compatibility). Please don't change it unless you know what
 
 # MULTI SERVER/VMs environment 
 #
 Vagrant.configure("2") do |config|
 # creating are Ansible controller
   config.vm.define "controller" do |controller|
     
    controller.vm.box = "bento/ubuntu-18.04"
    
    controller.vm.hostname = 'controller'
    
    controller.vm.network :private_network, ip: "192.168.33.12"
    
    # config.hostsupdater.aliases = ["development.controller"] 
    
   end 
 # creating first VM called web  
   config.vm.define "web" do |web|
     
     web.vm.box = "bento/ubuntu-18.04"
    # downloading ubuntu 18.04 image
 
     web.vm.hostname = 'web'
     # assigning host name to the VM
     
     web.vm.network :private_network, ip: "192.168.33.10"
     #   assigning private IP
     
     #config.hostsupdater.aliases = ["development.web"]
     # creating a link called development.web so we can access web page with this link instread of an IP   
         
   end
   
 # creating second VM called db
   config.vm.define "db" do |db|
     
     db.vm.box = "bento/ubuntu-18.04"
     
     db.vm.hostname = 'db'
     
     db.vm.network :private_network, ip: "192.168.33.11"
     
     #config.hostsupdater.aliases = ["development.db"]     
   end
 
 
 end
```

- type the following into terminal: ```vagrant up```
- type ```vagrant status``` - to see if the different vms are running
- go to gitbash and type: vagrant ssh controller [do this for web and db vms]
- once you have logged into the vm:
```
sudo apt update -y
sudo apt upgrade -y
env [should see USER=vagrant]
sudo ansible --version [this hasnt been installed yet, so should say that it doesnt exists]
python --version
sudo apt install software-properties-common
sudo apt-add-repository ppa:ansible/ansible [ go to location and download it - this is specifically for anseible ]
sudo apt update -y
sudo apt install ansible 
sudo ansible --version
ssh vagrant@192.168.33.10 [this enables you to ssh into the web vm from the controller vm]
password: vagrant
exit [to exit the web vm]
pwd
```
<img width="356" alt="image" src="https://github.com/MutiatOba/IaC/assets/118978642/a95fbc51-7e5e-4db6-95e4-3c24ecdacf0b">

Once you install ansible, you get the ansible default dir structure
- ```/etc/ansible``` - in there have hosts file and ansible.cfg
ansible hosts = when you want to communicate with agent, it goes to host and looks for the agent. so you need to update the host file with details of the agent 
The aim is to be able to run a command in controller for one of the agents without having to ssh into the actual agent 

### configure the host
- open bash
- ssh into controller ¬¬¬vagrant ssh controller```
- cd /etc/ansible/
- ls [should see hosts file and cfg]
- sudo apt install tree - see directory in tree form
- sudo ansible all -m ping - means all node -m (module) module is ping [ will tell us the host file is empty - so need to inform the host file of the agents]
- ```ssh vagrant@192.168.33.10``` - check if can ssh to web
- password: vagrant 
- update the web vm ```sudo apt update - y```
- upgrade the web vm ```sudo apt upgrade -y```
- exit [to go back to the controller]

run the same steps for the db vm:
- ssh vagrant@192.168.33.11 - check if can ssh to db
- password: vagrant 
- sudo apt update - y
- sudo apt upgrade -y
- exit [to go back to the controller]

These steps show that we can ssh and we have establised a network

Need to test if controller can ping the machines
- make sure in /etc/ansible/
- ```sudo ansible all -m ping``` - means all node -m (module) module is ping [ will tell us the host file is empty - so need to inform the host file of the agents]

Need to tell controller who the agents are:
- ```sudo nano hosts```
- create a group name web in the hosts file:

```[web]
192.168.33.10 ```

- then type exit 
- sudo ansible web -m ping
- will get an error - when ssh into a vm we use password to authenticate. when we ping we havent provided password or key, so we get an error. so need to communicate using key or password. to solve it need to provide a way to authtenticate:

- sudo nano hosts
```[web]
192.168.33.10 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant```

- then exit 

- ```sudo ansible web -m ping``` [should get a successful result] 

configure the same way for the db vm: 
- sudo nano hosts
```[db]
192.168.33.11 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant```

for this to work, we need to update the config file and make the following update under [defaults]. ```sudo nano ansible.cfg```, then type this in 

```host_key_checking = false```
when you run ```sudo ansible all -m ping``` you should get a positive outcome.

### adhoc commands

You can run linux commands from the controller to the agent.

- ssh into web from the controller vm, run the date command and display in the controller: ```sudo ansible web -a "date"```

- can run the same command on all agents: ```sudo ansible all -a "date"```

- Want to know more about the servers
```sudo ansible all -a "free"``` tells you how much free space each server has

- say want data transferred to agents but we dont know what is there: ```sudo ansible all -a "ls"```

- to transfer a file from controller to web agent: ``` sudo ansible web -m copy -a "src=/etc/ansible/testing.txt dest=/home/vagrant"```
