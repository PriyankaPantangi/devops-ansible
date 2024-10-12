# Launch centos server
k run webserver1 --image brainupgrade/rhel-ssh-ansible:20241012 -- tail -f /dev/null

# Launch centos for postgresql installation
k run postgresql1 --image brainupgrade/rhel-ssh-ansible:20241012 -- tail -f /dev/null

# Launch playbook
ansible-playbook -i inventory.ini playbook.yml