# Ansible Debian Nginx Role 

This repository contains an Ansible role for installing [Nginx](https://nginx.org/en/) on Debian servers.

To use this role you need to use Ansible Galaxy to install it into another repository under `galaxy/roles/nginx` by adding a `requirements.yml` file in that repo that contains:

```yml
---
- name: nginx
  src: https://git.coop/webarch/nginx.git
  version: master
  scm: git
```

And a `ansible.cfg` that contains:

```
[defaults]
retry_files_enabled = False
pipelining = True
inventory = hosts.yml
roles_path = galaxy/roles

```

And a `.gitignore` containing:

```
roles/galaxy
```

To pull this repo in run:

```bash
ansible-galaxy install -r requirements.yml --force 
```

The other repo should also contain a `nginx.yml` file that contains:

```yml
---
- name: Install Nginx
  become: yes

  hosts:
    - nginx_servers

  roles:
    - nginx
```

And a `hosts.yml` file that contains lists of servers, for example:

```yml
---
all:
  children:
    nginx_servers:
      hosts:
        host3.example.org:
        host4.example.org:
        cloud.example.com:
        cloud.example.org:
        cloud.example.net:
```

Then it can be run as follows:

```bash
ansible-playbook nginx.yml 
```
