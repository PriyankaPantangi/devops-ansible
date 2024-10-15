# Launch rhel server for webserver installation
k run centos --image brainupgrade/ansible-node-centos:20241016v3 --privileged
k expose pod centos --port 22 --target-port 22

# add ssh key 
ssh-copy-id root@centos.<username>

# Download the nginx role
ansible-galaxy role install geerlingguy.nginx
# Launch playbook
ansible-playbook -i inventory.ini playbook.yml

# Verification
ansible all -m command -a "systemctl status nginx" -i inventory.ini  --user root