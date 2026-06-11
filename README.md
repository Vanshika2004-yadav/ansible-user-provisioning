# AWS User Provisioning Automation

## Objective

Automate Linux user provisioning using Ansible.

## Features

- Create developers group
- Create users:
  - user1
  - user2
  - user3
- Add users to developers group
- Create home directories
- Deploy SSH public keys
- Configure password expiration policy
- Validate users existence

## Project Structure

```
user-management-ansible/
├── inventories/
├── playbooks/
├── roles/
│   └── user_management/
│       ├── defaults/
│       ├── files/
│       ├── tasks/
│       └── vars/
└── ansible.cfg
```

## Run Playbook

```bash
ansible-playbook playbooks/site.yml
```

## Validation

```bash
ansible target -m command -a "id user1"
ansible target -m command -a "id user2"
ansible target -m command -a "id user3"
```
