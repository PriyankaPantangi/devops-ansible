# Launch centos/systemd managed node
k apply -f centos-systemd.yaml
k expose pod node-network1 --port 22 --target-port 22

ssh-copy-id root@node-network1

# Run playbook
ansible-playbook -i inventory.ini playbook.yml