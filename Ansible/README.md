# Autoscript for setup cluster

# Install package
### Install pip3
```
sudo apt install python3-pip

or

curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
sudo python3 get-pip.py
```


### Install Ansible
```
python3 -m pip install --user ansible
```

### Comfirmed Ansible that installed
```
ansible --version
```