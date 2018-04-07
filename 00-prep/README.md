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

pip install ansible

echo 'PATH=$HOME/.local/bin:$PATH' >> ~/.bashrc
```



