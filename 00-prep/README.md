# Windows 10 Prep

On Windows 10 Pro Version 1709 Build 16299.309

https://www.jeffgeerling.com/blog/2017/using-ansible-through-windows-10s-subsystem-linux

I already had the Windows Subsystem for Linux installed with Ubuntu so I started with the Installing Ansible section of the above mentioned blog post.

First had to retrieve new lists of packages due to an error when first trying to install python-pip:

```
sudo apt-get update
```

After performing the update, the python and lib installs were performed individually.

```
sudo apt-get -y install python-pip
sudo apt-get -y install python-dev
sudo apt-get -y install libffi-dev
sudo apt-get -y install libssl-dev

pip install ansible --user

echo 'PATH=$HOME/.local/bin:$PATH' >> ~/.bashrc
```

# Ansible Customizations

https://github.com/ansible/ansible/issues/11050

In ansible.cfg, the following config will disable colorized shell output:

```
nocolor=1
```

# Ansible Galaxy

First add the following (or your preferred variant, to your ~/.bashrc

```
export ANSIBLE_ROLES_PATH=$HOME/.ansible/roles
```

Then install what ever roles are required using ansible-galaxy

```
ansible-galaxy install elasticsearch
ansible-galaxy install geerlingguy.ntp
```


