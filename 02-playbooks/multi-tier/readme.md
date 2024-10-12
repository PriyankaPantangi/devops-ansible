# Setup managed node
kubectl run multitier --image brainupgrade/ubuntu-ssh-ansible:20241012 --env USERNAME=ubuntu --env PASSWORD=brainupgrade

kubectl expose pod multitier --port 22 --target-port 22

ssh-copy-id ubuntu@multitier


# Run playbook
ansible-playbook -i inventory.ini playbook.yml --ask-become-pass