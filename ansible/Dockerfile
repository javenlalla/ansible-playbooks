FROM ubuntu:latest

RUN apt update && \
    apt -y install software-properties-common && \
    add-apt-repository --yes --update ppa:ansible/ansible

RUN apt -y install ansible

# Additional dependencies.
RUN apt -y install \
    # sshpass required for password input when connecting with Ansible and using arguments such as "ansible_password". 
    sshpass

COPY hosts /etc/ansible/hosts

CMD ["tail", "-f", "/dev/null"]
