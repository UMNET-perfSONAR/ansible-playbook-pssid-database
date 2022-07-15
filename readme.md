# ansible-playbook-pssid-database

This is an Ansible Playbook for deploying [pSSID-database](https://github.com/UMNET-perfSONAR/pSSID-database), an [ELK stack](https://www.elastic.co/what-is/elk-stack) configured for usage by [pSSID](https://github.com/UMNET-perfSONAR/pSSID), to a server. It installs Docker and then the ELK stack itself.

## Usage

1. `git clone` this repository.
1. Run `ansible-galaxy install -r requirements.yml` to get the Playbook's dependencies.
1. Run `ansible-playbook playbook.yml -i 1.1.1.1,` to flash machine `1.1.1.1`. Note the trailing comma.
    * Optionally append ` -e 'destination=/my/path repository=git://my-repo'` to the command to override the default destination path and remote repository.
