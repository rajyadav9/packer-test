Ansible Role for AWSCLI
-----------------------
A really simple Ansible role which installs the AWS CLI with all the required dependencies on Ubuntu 14.04 LTS, it should work on other versions of Ubuntu too.

### Requirements
User(s) must exist on the target system and home directory must reside under /home directory 

Edit the `site.yml` file, mentioned this role:

```yaml
---
 - hosts: server
   sudo: True
   gather_facts: True
   roles:
     - awscli 
```
After that edit the `vars/main.yml` file:

> Change the username(s), their default aws region, output format, aws access key and aws secret key but these user(s) must exist on the target system. Also change the other values as per your requirement. These are self explanatory.

```yaml
---
awscli_users:
  - username: phg
    state: present
    awscli: 
        aws_region: us-east-1
        aws_output_format: json # format can be 'text','table' and 'json'
        aws_access_key_id: ''
        aws_secret_access_key: ''
  - username: vagrant
    state: present
    awscli: 
        aws_region: us-east-1
        aws_output_format: table # format can be 'text','table' and 'json'
        aws_access_key_id: ''
        aws_secret_access_key: ''
```
Best option is to encrypt the variables file(vars/main.yml) by using the following command:

```
ansible-vault encrypt vars/main.yml
```

Then run this command:

```
ansible-playbook -i hosts -u phg site.yml
```
**Note:** Please don't forget to change `phg` with your username
