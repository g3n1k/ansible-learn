# ansible-learn
my learn ansible

## 01. adhoc command
in this learn i have 2 linux machine, debian 9 and centos 8, using custom hosts file as inventory 
````
cat hosts
````
centos 8 come with `/usr/bin/python3` not `/usr/bin/python` so we need add `ansible_python_interpreter="/usr/bin/python3"` in **cent8** line

execute with command 
````
cd ansible-learn
ansible server -m ping -i hosts
ansible deb -m ping -i hosts
ansible cent -m ping -i hosts

````