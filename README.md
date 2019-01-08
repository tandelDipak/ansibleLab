# ansibleLab
Using docker container create a network of ubuntu containers on which person can test ansible playbook. 

First build two image using below commands

cd /abc/xyz (move to your ansible_controller folder)
docker build -t ansible_controller:v1 .

cd /abc/xyz (move to your nodes folder)
docker build -t nodes:v1 .


Create one container from ansible_controller and atleast one from nodes using below commands.

#For ansible_controller 
docker run -p 22 --rm -ti --name ac --network ex ansible_controller:v1 bash

#For nodes
docker run -p 22 --rm -ti --name n1 --network ex nodes:v1 bash

Run below command in all containers
/usr/sbin/sshd
su - ansible

On container ac 
ssh-keygen

Now copy public key on all nodes using
ssh-copy-id n1 (run once for each node)

#perfome below action on ansible controller container
sudo apt-get install vim
mkdir ping
cd ping
touch ansible.cfg

#copy this content in a ansible.cfg

[defaults]
remote_user = ansible
host_key_checking = false
inventory = inventory

[privilege_escalation]
become = True
become_method = sudo
become_user = root
become_ask_pass = False

[ssh_connection]
pipelining=True