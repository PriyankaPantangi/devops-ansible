# Setup - Control Node
sudo apt update
sudo apt install ansible -y
ansible --version

# Generate RSA key
ssh-keygen -t rsa