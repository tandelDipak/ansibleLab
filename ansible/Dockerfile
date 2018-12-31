# Download base image ubuntu 16.04
FROM ubuntu:16.04

# Update Ubuntu Software repository
RUN apt-get update

# Install netcat, ssh and iputils-ping
RUN apt-get install -y netcat ssh iputils-ping sudo

# Set root password as root
RUN echo "root:root" | chpasswd

# Make directory for sshd
RUN mkdir /var/run/sshd

# change permission of that directory
RUN chmod 0755 /var/run/sshd  

# Add user ansible into sudo group
RUN useradd --create-home --shell /bin/bash --groups sudo ansible

# Set password for user ansible
RUN echo "ansible:ansible" | chpasswd

# Create file in sudoers.d
RUN touch /etc/sudoers.d/ansible

# Add line into ansible file
RUN echo "ansible ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers.d/ansible

# expose port 22
EXPOSE 22

# Enter below command in bash /usr/sbin/sshd