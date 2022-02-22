# Ansible Playbooks

## Overview

This repository can be used to establish an integration between Ansible and a targeted server(s) and run `Playbooks`.

## Setup

### Update `hosts` File

```bash
cp ansible/hosts.sample ansible/hosts
vi ansible/hosts
```

### Build And Initialize Container

```bash
docker build ansible -f=ansible/Dockerfile --tag=ansible:executor
docker-compose -f=ansible/docker-compose.yml up -d
```

### Hook Into Container

```bash
docker exec -it ansible-executor bash
```

## Testing Playbooks Locally

If desired, `Playbooks` can be tested locally against the `Testing Target` container before executing on remote servers. Build and spin up the container with the following commands.

```bash
docker build ansible -f=ansible/Dockerfile.testing-target --tag=ansible-testing-target
docker-compose -f=ansible/docker-compose.testing-target.yml up -d
```

### Connecting Via Root User

The password for the `root` user configured in the `Testing Target` container is: `password`

With that information, the testing node can be added to the `hosts` file as follows:

```plain
testing-target ansible_host=test
```

## Helpful Commands

### Test Managed Nodes Connections

```bash
ansible all -m ping
```

### Verify Managed Nodes Python Version

```bash
ansible all -a "python3 --version"
```

## To Improve

- Make username and group values dynamic using variables within the `docker` playbook
