# AWS

## aws-ec2-centos7.yml

Creates a single EC2 instance using the CentOS 7 AMI from the AWS Marketplace

More Infe on the CentOS AMI: https://wiki.centos.org/Cloud/AWS

If the error "boto required for this module" then run the following to install the boto package. 
This was required before the ec2 task would run.

```
pip install boto
```

_Note_: Change the `group`, `vpc_subnet_id`, `key_name`, and `region` as appropriate for your deployment.


### ec2_instance_facts 

ec2_instance_facts requires boto3 per https://docs.ansible.com/ansible/devel/modules/ec2_instance_facts_module.html

```
pip install boto3
```

### SSH and Fingerprint Authenticity

https://stackoverflow.com/questions/32297456/how-to-ignore-ansible-ssh-authenticity-checking

Refer to ansible.cfg `host_key_checking`, but the ssh-keyscan suggestion in the above linked stackoverflow article is a better solution.