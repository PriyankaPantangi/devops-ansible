# Launch centos/systemd managed node
kubectl run nodenetwork1 --image brainupgrade/ubuntu-ssh-ansible:20241012 --env USERNAME=ubuntu --env PASSWORD=brainupgrade
k expose pod nodenetwork1 --port 22 --target-port 22

ssh-copy-id ubuntu@nodenetwork1.<username>

# Run playbook
ansible-playbook -i inventory.ini playbook.yml --ask-become-pass