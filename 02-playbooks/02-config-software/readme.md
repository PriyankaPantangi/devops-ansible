# Launch the webserver to be configured

kubectl run nodeconfig --image brainupgrade/ubuntu-ssh-ansible:20241012 --env USERNAME=ubuntu --env PASSWORD=brainupgrade

# Copy id onto managed nodes
ssh-copy-id ubuntu@nodeconfig

# Run     playbook
ansible-playbook -i inventory.ini playbook.yml