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
## 02. Update with ansible-playbook

this section, we will choose deb9, single host, not group server  
this code just update via apt, i comment centos, becouse centos 8 use python3 as default
and its uncompatible with ansible yum wich using python2

this section we need enable authorized_keys to user root `sudo cp .ssh /root/ -R`  

````
ansible-playbook update.yml -l deb9
````

## 03. Install docker and docker-compose 
using **docker-var.yml** to store value and calling from `install-docker.yml`
````
ansible-playbook install-docker.yml -l deb9
````

## 04. Install ufw
now lets install ufw
````
ansible-playbook install-ufw.yml -l deb9
````

## 05. Setup ufw to allow ssh, http & https 
config ssh http https
if you want check systax, add `--check` options
````
ansible-playbook ufw-enable-port.yml -i hosts.dev --check
ansible-playbook ufw-enable-port.yml -i hosts.dev
````


## 06. Setup Fail2ban
secured again with fail2ban
````
ansible-playbook install-fail2ban.yml -l deb9
````
we can read who connect to server with command `sudo tail -f /var/log/auth.log`  

and we can view realtime from fail2ban `sudo tail -f /var/log/fail2ban.log `

## 05. git clone
clone repo with ansible-playbook

<!-- 
## 06. start stop restart docker-compose

## 07. pull from repo --> -->
