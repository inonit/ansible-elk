
# Ansible deployment for ELK (Elasticsearch, Logstash, Kibana) on Vagrant and EC2

Contains ansible scripts for settings ut ELK on Vagrant and AWS EC2.
Based on Mitchell Ancias' article from [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-4-on-ubuntu-14-04).

## Vagrant Provisioning

**Requirements**

- Ansible
- Vagrant
- [Vagrant::Hostupdater](https://github.com/cogitatio/vagrant-hostsupdater)

**Running**

    $ vagrant up
    

## EC2 Provisioning

**Requirements**

- Ansible
- Boto

**Configure**

1. Make sure you have your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables is set.

    ```
    $ export AWS_ACCESS_KEY_ID=MyAccessKeyID
    $ export AWS_SECRET_ACCESS_KEY=MySuperSecretAccessKey
    ```

2. Disable host key checking: 

    `$ export ANSIBLE_HOST_KEY_CHECKING=False`

3. Log into the AWS Console and create a new Key pair called `elk-node`. Download the PEM certificate and 
   place it in your ~/.ssh directory. Remember to `chmod 400 elk-node.pem`.

4. Run the playbook.
    
    ```
    $ ansible-playbook -i hosts --tags "setup" ec2.yml
    ....
    working...
    ...
    
    $ ansible-playbook -i hosts --tags "provision" ec2.yml
    ...
    working...
    ...
    ```
    
Once done, check your `hosts` file for the public DNS address for your newly created server.
Point your web browser at this address, and you should be good to go.

## Security

**The default setup is wide open, so you'll have to secure your server with .htaccess or other means!**


