# Launch centos server
k run webserver1 --image brainupgrade/rhel-ssh-ansible:20241012 
k expose pod webserver1  --port 22 --target-port 22

# Launch centos for postgresql installation
k run postgresql1 --image brainupgrade/rhel-ssh-ansible:20241012
k expose pod postgresql1 --port 22 --target-port 22

# Launch playbook
ansible-playbook -i inventory.ini playbook.yml