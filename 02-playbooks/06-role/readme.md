# Launch rhel server for webserver installation
k run servernginx --image brainupgrade/rhel-ssh-ansible:20241012 

k expose pod servernginx  --port 22 --target-port 22

# add ssh key 
ssh-copy-id root@servernginx.<username>

# Launch playbook
ansible-playbook -i inventory.ini playbook.yml