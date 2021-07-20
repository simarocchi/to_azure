FROM ubuntu:20.04

ENV TZ=Europe/Bologna

RUN apt update && apt -y upgrade  
RUN apt -y install python3-pip
RUN DEBIAN_FRONTEND="noninteractive" apt -y install openssh-server
RUN systemctl enable ssh

#configure ssh 

RUN echo "Port 2222" > /etc/ssh/sshd_config
RUN echo "ListenAddress 0.0.0.0" >> /etc/ssh/sshd_config
RUN echo "LoginGraceTime 180" >> /etc/ssh/sshd_config
RUN echo "X11Forwarding yes" >> /etc/ssh/sshd_config
RUN echo "Ciphers aes128-cbc,3des-cbc,aes256-cbc,aes128-ctr,aes192-ctr,aes256-ctr" >> /etc/ssh/sshd_config
RUN echo "MACs hmac-sha1,hmac-sha1-96" >> /etc/ssh/sshd_config
RUN echo "StrictModes yes" >> /etc/ssh/sshd_config
RUN echo "SyslogFacility DAEMON" >> /etc/ssh/sshd_config
RUN echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config
RUN echo "PermitEmptyPasswords no" >> /etc/ssh/sshd_config
RUN echo "PermitRootLogin yes" >> /etc/ssh/sshd_config
RUN echo "Subsystem sftp internal-sftp" >> /etc/ssh/sshd_config

# azure login configuration
RUN echo "root:Docker!" | chpasswd

# Open port 2222 for SSH access

EXPOSE 80 2222

# General environment variables
ENV NAME_CONTAIN=vm_carrozzata

