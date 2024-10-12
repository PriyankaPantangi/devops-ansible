# Setup managed node
kubectl run multitier --image brainupgrade/ansible-node-centos:20241012

kubectl run multitier --image brainupgrade/docker:27-dind-20240817 --privileged

kubectl expose pod multitier --port 22 --target-port 22

ssh-copy-id root@multitier


# Run playbook
ansible-playbook -i inventory.ini playbook.yml