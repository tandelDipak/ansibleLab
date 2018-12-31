# Download base image ubuntu 16.04
FROM ubuntu:16.04

# Update Ubuntu Software repository
RUN apt-get update

# Install netcat, ssh and iputils-ping
RUN apt-get install -y netcat ssh iputils-ping

# expose port 22
EXPOSE 22

# Print Netcat + Ssh installed
CMD echo "Netcat + Ssh"