# Launch rhel server for webserver installation
k run webserver1 --image brainupgrade/rhel-ssh-ansible:20241012 

k expose pod webserver1  --port 22 --target-port 22

# Launch rhel server for postgresql installation
k run postgresql1 --image brainupgrade/rhel-ssh-ansible:20241012
k expose pod postgresql1 --port 22 --target-port 22

# add ssh key 
ssh-copy-id root@webserver1.<username>
ssh-copy-id root@postgresql1.<username>

# Launch playbook
ansible-playbook -i inventory.ini playbook.yml