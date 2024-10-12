# Dockerfile to Simulate an Ansible Managed Node with SSH and Yum

# Base Image - RHEL (Red Hat Enterprise Linux)
FROM registry.access.redhat.com/ubi8/ubi:latest

# Install OpenSSH Server, SSH Client, and other utilities
RUN yum update -y && \
    yum install -y openssh-server openssh-clients && \
    yum install -y sudo && \
    yum clean all && \
    mkdir /var/run/sshd && \
    ssh-keygen -A

# Set root password
RUN echo 'root:password' | chpasswd

# Allow root login via SSH
RUN sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# Start SSH service
EXPOSE 22

# Command to run SSH Daemon
CMD ["/usr/sbin/sshd", "-D"]

# docker build -t brainupgrade/rhel-ssh-ansible:20241012 .
# docker run -d  brainupgrade/rhel-ssh-ansible:20241012
