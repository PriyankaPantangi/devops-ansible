# Dockerfile for Managed Node to Run Multi-Tier Application Playbook

# Base Image
FROM centos:8

RUN sed -i.bak 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i.bak 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-* 


# Install system utilities, SSH, and Python
RUN yum update -y && \
    yum install -y sudo wget curl systemd iproute openssh-server openssh-clients python3 net-tools procps-ng && \
    ssh-keygen -A

# Enable SSH access
RUN mkdir /var/run/sshd && \
    echo 'root:password' | chpasswd && \
    sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config && \
    systemctl enable sshd

# Start SSH Daemon and keep the container running
CMD ["/usr/sbin/sshd", "-D"]

# docker build -t brainupgrade/ansible-node-centos:20241012 .
