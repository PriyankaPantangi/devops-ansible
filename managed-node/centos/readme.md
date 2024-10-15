# Launch centos node (root/password)
k run centos --image brainupgrade/ansible-node-centos:20241016v3 --privileged
k expose pod centos --port 22 --target-port 22

ssh-copy-id root@centos.<username>

