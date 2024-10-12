# Launch centos/systemd managed node
k apply -f centos-systemd.yaml
k expose pod node-network1 --port 22 --target-port 22