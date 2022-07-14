# ansible-playbook-pssid-database

This is an Ansible Playbook for deploying [pSSID-database](), an [ELK stack]() configured for usage by [pSSID]() to a server. It installs Docker and then the ELK stack itself.

## Getting Dependencies

```
ansible-galaxy install -r requirements.yml
```

## Running

```
ansible-playbook playbook.yml -i 1.1.1.1,
```

Change `1.1.1.1` to the IP address of the intended target, but take note of the trailing comma.
