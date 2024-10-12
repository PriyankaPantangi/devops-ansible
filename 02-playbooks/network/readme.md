# Launch centos/systemd managed node
kubectl run nodenetwork1 --image brainupgrade/rhel-ssh-ansible:20241012
k expose pod nodenetwork1 --port 22 --target-port 22

ssh-copy-id root@nodenetwork1

# Run playbook
ansible-playbook -i inventory.ini playbook.yml