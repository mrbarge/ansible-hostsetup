host-setup
==========

Home shell environment setup.

## Setup

### Fetch the repo

Clone into the Ansible role directory of your choice.

```bash
$ git clone https://github.com/mrbarge/host-setup.git roles
```

### Create the inventory

```bash
$ vi ansible.host
```

```ini
[all]
my-dev-host 
```

Make the `host_vars` directory where *ansible.host* file is located.

```bash
$ mkdir host_vars
```

Create a file in the newly created directory matching your host.

```bash
$ cd host_vars
$ vi my-dev-host
```

with

```yaml
---
dest_user: 'my-user-name'
```

### Run the playbook

Create a playbook to call the host-setup role, called *host-setup.yml*

```yml
- name: Host setup
  hosts: all
  sudo: yes
  roles:
    - host-setup
```

Use *ansible.host* as inventory. 

```bash
$ ansible-playbook -i ansible.host host-setup.yml
```

