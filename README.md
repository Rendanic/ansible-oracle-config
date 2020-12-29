# ansible-oracle example configurations


## AWS


### ansible-oracle Playbooks

    ansible-playbook -i inventory/aws -u ec2-user os.yml -e hostgroup=tag_ansible_oracle_oratest

### gossm

    wget https://github.com/gjbae1212/gossm/releases/download/v1.1.1/gossm_1.1.1_Linux_x86_64.tar.gz

### Docker Container for Ansible + boto

    sudo sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod a+x /usr/local/bin/docker-compose
    usermod  -a -G docker ec2-user

    docker-compose run -u ${USER} --rm ansible bash