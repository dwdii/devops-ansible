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

### SSH Private Key

https://stackoverflow.com/questions/33795607/how-to-define-ssh-private-key-for-servers-fetched-by-dynamic-inventory-in-files

Refer to ansible.cfg `private_key_file`, but the above linked stackoverflow article provides some other options as well.

```
WARNING: UNPROTECTED PRIVATE KEY FILE!
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0777 for '/mnt/c/Users/Dan/.../key.pem are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "/mnt/c/Users/Dan/.../key.pem": bad permissions
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
```

Received the above warning about my private key... have since rectified this. 
One step was to copy the pem file to my linux subsystem user's home directory, and 
chmod to apply acceptable permissions. 

https://stackoverflow.com/questions/9270734/ssh-permissions-are-too-open-error

```
chmod 600 ~/key.pem
```