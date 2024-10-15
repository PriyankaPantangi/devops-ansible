## Launch managed node
kubectl run ubuntuapache --image brainupgrade/ubuntu-ssh-ansible:20241012 --env USERNAME=ubuntu --env PASSWORD=brainupgrade

## Configure SSH on managed nodes
ssh-keygen -t rsa
ssh-copy-id ubuntu@ubuntuapache


# Run playbook
ansible-playbook -i inventory.ini install_apache.yml --ask-become-pass --become-method=sudo 

# Verification
ssh ubuntu@ubuntuapache
sudo service apache2 status

## Alternate 
ansible webservers -m command -i inventory.ini -a "service apache2 status"

<managed-node-ip>:<port>    

# Other commands

## Verify inventory
ansible-inventory -i inventory.ini --list

## Ping host group
ansible webservers -u ubuntu -m ping -i inventory.ini 

ansible webservers -i inventory.ini -m ping --ask-become-pass  --become-method=sudo

## Display inventory info
 <!-- ansible-playbook -i inventory.ini install_apache.yml --ask-become-pass --become-method=sudo  -->

## Display modules and other useful info
ansible-doc -l

## Service Status of SSH server
ansible all -a "service ssh status" --become-method=sudo --ask-become-pass -i inventory.ini

## Restart apache2
ansible webservers -m ansible.builtin.service -a "name=apache2 state=restarted" -i inventory.ini

## Gathering system info / facts
ansible all -m ansible.builtin.setup -i inventory.ini 