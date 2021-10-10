# Ansible Playbooks

## Overview

This repository can be used to establish an integration between Ansible and a targeted server(s) and run `Playbooks`.

## Prepare Image Build

### Update `hosts` File

```bash
cp ansible/hosts.sample ansible/hosts
vi ansible/hosts
```

## Build Image

```bash
docker build ansible -f=ansible/Dockerfile --tag=ansible:executor
```

## Hook Into Container

```bash
docker exec -it ansible-executor bash
```

## To Improve

- Make username and group values dynamic using variables within the `docker` playbook

## Helpful Commands

### Test Managed Nodes Connections

```bash
ansible all -m ping
```

### Verify Managed Nodes Python Version

```bash
ansible all -a "python3 --version"
```
