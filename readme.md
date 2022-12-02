# ansible-playbook-pssid-database

This is an Ansible Playbook for deploying [pSSID-database](https://github.com/UMNET-perfSONAR/pSSID-database), an [ELK stack](https://www.elastic.co/what-is/elk-stack) configured for usage by [pSSID](https://github.com/UMNET-perfSONAR/pSSID), to a server. It installs Docker and then the ELK stack itself.

## Clone this playbook

```
git clone https://github.com/UMNET-perfSONAR/ansible-playbook-pssid-database.git
cd ansible-playbook-pssid-database
```

```
cp .env.example .env
vi .env
```

```
ansible-vault encrypt .env
```

## Getting Dependencies

```
ansible-galaxy install -r requirements.yml
```

```
ansible-playbook playbook.yml \
  -i IP_ADDR,
```

```
cp archiver.json.example archiver.json
vi archiver.json
```



## Usage

(`1.1.1.1` is used in place of the database server's IP address throughout.)

1. `git clone` this repository.
1. Run `cp .env.example .env`, `vi .env`, and `ansible-vault encrypt .env` to generate a `.env` file. Leave `ELASTIC_VERSION` and make the other settings random strings.
1. Run `ansible-galaxy install -r requirements.yml` to get the Playbook's dependencies.
1. Run `ansible-playbook playbook.yml -i 1.1.1.1,` to deploy to the target. Note the trailing comma.
    * Optionally append ` -e 'destination=/my/path repository=git://my-repo'` to the command to override the default destination path and remote repository from which to deploy.
1. Give the stack roughly a minute to come up.
1. Run `cp archiver.json.example archiver.json` and change out `1.1.1.1` in `archiver.json`. Then, to test that archiving from pScheduler is working, run `pscheduler task --archive @./archiver.json rtt --dest www.perfsonar.net`.
1. Open a browser and go to `http://1.1.1.1:5601/app/discover`. Log in with username `elastic` and password as whatever you put as the `ELASTIC_PASSWORD` setting within `.env`. If the page says `You have data in Elasticsearch. Now, create a data view.` (as opposed to `Welcome to Analytics!`) everything is set up correctly.
