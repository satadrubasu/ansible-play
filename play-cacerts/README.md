## Pre-requisite

1. The Base Ubuntu image should be of 20.04 focal ( choose AMI as per )

##
This playbook will Install docker engine based installs of
  Nginx , Jenkins , Custom PATS Reporting plugin for jenkins.
  Ensure jenkins is over https for AWS installs * via nginx )
  
  

## Usage

|Step #|Details|
|---|---|
|Step 1|Configure the detals of the target host on file ./host_vars/target_jenkins|
|Step 2|run command - ansible-playbook site.yml|
  > ansible-playbook site.yml  

 After first time provisioning , the secret pwd can be found the following way :  
 - ssh to the machine with the key used.
 - sudo su
 - docker ps -a
 - docker logs <containerid-of-jenkins>   
     OR  
 - cat /root/docker_host_mnt/jenkins/home/secrets/initialAdminPassword
 - continue steps as needed.
 - open the jenkins instance in browser by going to public ip assigned. 
   

### EC2 details ?

1. EC2 type t2.xlarge 
2. Base AMI - ubuntu-focal 20.04
3. Role - patsvm

