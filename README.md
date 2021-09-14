This project has been archived.

Please use the new project: https://github.com/opitzconsulting/ansible-oracle-inventory



# ansible-oracle example configurations

## Oracle GoldenImage

    $ORACLE_HOME/runInstaller -createGoldImage -silent -destinationLocation "${ORACLE_BASE}/db_golden_image"

## getMOSPatch

    wget -O ~/getMOSPatch.jar  https://github.com/MarisElsins/getMOSPatch/raw/master/getMOSPatch.jar
    java -jar ~/getMOSPatch.jar  platform=226P download=all patch= MOSUser=

## AWS


### ansible-oracle Playbooks

    ansible-playbook -i inventory/aws -u ec2-user os.yml -e hostgroup=tag_ansible_oracle_oratest

#### Patches 19.9 on top of 19.3

    ansible-playbook -i inventory/aws -u ec2-user swdb.yml -e hostgroup="tag_db19_3fs" -e db_home_name=db199 -e oracle_home=/u01/app/oracle/product/19c/19.3

#### Patches 18.12 on top of 18.8

    ansible-playbook -i inventory/aws -u ec2-user swdb.yml -e hostgroup="tag_db18_latestfs" -e db_home_name=db1812 -e oracle_home=/u01/app/oracle/product/18c/latest

### gossm

    wget https://github.com/gjbae1212/gossm/releases/download/v1.1.1/gossm_1.1.1_Linux_x86_64.tar.gz

### Docker Container for Ansible + boto

    sudo sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod a+x /usr/local/bin/docker-compose
    sudo usermod  -a -G docker ec2-user

    docker-compose run --rm ansible bash
