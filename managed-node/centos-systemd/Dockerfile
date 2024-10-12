# Base Image
FROM centos/systemd

RUN sed -i.bak 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i.bak 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-* 

# Install OpenSSH Server, SSH Client, and other utilities
RUN yum update -y && \
    yum install -y openssh-server openssh-clients && \
    yum install -y sudo && \
    yum clean all && \
    mkdir /var/run/sshd && \
    systemctl enable sshd && \
    ssh-keygen -A
    

# Set root password for SSH access
RUN echo 'root:password' | chpasswd

# Allow root login via SSH
RUN sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# Ensure that SSHD runs with an absolute path
RUN ln -sf /usr/sbin/sshd /usr/bin/sshd

# Expose SSH Port
EXPOSE 22

# Start SSH service explicitly after systemd initialization
STOPSIGNAL SIGRTMIN+3
CMD ["/usr/sbin/init"]

# Run SSH Daemon after systemd initialization
RUN systemctl enable sshd

# docker build -t brainupgrade/centos-systemd:20241012 .
# docker run -d brainupgrade/centos-systemd:20241012 