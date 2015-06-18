
# Ansible deployment for ELK (Elasticsearch, Logstash, Kibana) on a Vagrant box.

Contains ansible scripts for settings ut ELK on Vagrant and AWS EC2.
Based on Mitchell Ancias' article from [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-4-on-ubuntu-14-04)

## Vagran Provisioning

### Requirements

- Ansible
- Vagrant
- [Vagrant::Hostupdater](https://github.com/cogitatio/vagrant-hostsupdater)

### Running

    $ vagrant up
    

## EC2 Provisioning

### Requirements

- Ansible
- Boto

### Configure

Make sure you have your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment
variables is set.
