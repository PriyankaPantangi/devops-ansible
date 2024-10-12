# Dockerfile for Ubuntu-based SSH Server to be used as Ansible managed nodes

# Base Image
FROM ubuntu:latest

# Install OpenSSH Server and sudo
RUN apt-get update && \
    apt-get install -y openssh-server sudo && \
    mkdir /var/run/sshd && \
    apt-get clean

# Allow password authentication
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# Expose the SSH port
EXPOSE 22

# Start the SSH service
CMD ["/bin/bash", "-c", "id -u $USERNAME &>/dev/null || useradd -m -s /bin/bash $USERNAME; echo \"$USERNAME:$PASSWORD\" | chpasswd && usermod -aG sudo $USERNAME && /usr/sbin/sshd -D"]

# docker build -t brainupgrade/ubuntu-ssh-ansible:20241012 .
# docker run -d -e USERNAME=ubuntu -e PASSWORD=brainupgrade -p 22:22 brainupgrade/ubuntu-ssh-ansible:20241012

