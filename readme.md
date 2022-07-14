# ansible-playbook-pssid-database

This is an Ansible Playbook for deploying [pSSID-database](https://github.com/UMNET-perfSONAR/pSSID-database), an [ELK stack](https://www.elastic.co/what-is/elk-stack) configured for usage by [pSSID](https://github.com/UMNET-perfSONAR/pSSID), to a server. It installs Docker and then the ELK stack itself.

## Getting Dependencies

```
ansible-galaxy install -r requirements.yml
```

## Running

```
ansible-playbook playbook.yml -i 1.1.1.1,
```

Change `1.1.1.1` to the IP address of the intended target, but take note of the trailing comma.
