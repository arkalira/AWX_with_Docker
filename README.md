# AWX_with_Docker

Use Ansible AWX with docker-ce over Debian 9. 

- Prerequisites: 
 - At least 4GB of memory.
 - At least 2 cpu cores.
 - At least 20GB of space.
 - Running Docker, Openshift, or Kubernetes.

## Install Docker 
```
apt-get remove docker docker-engine docker.io
apt-get install \\n apt-transport-https \\n ca-certificates \\n  curl \\n  gnupg2 \\n software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
apt-key fingerprint 0EBFCD88\n
add-apt-repository \\n "deb [arch=amd64] https://download.docker.com/linux/debian \\n   $(lsb_release -cs) \\n   stable"
apt update && apt-get install docker-ce
```

## Install Ansible

```
apt install python-pip
pip install ansible
```

## Ansible AWX Install

```
git clone https://github.com/ansible/awx.git
cd awx/
git clone https://github.com/ansible/awx-logos.git
pwd
```

Returns: /root/awx

```
cd installer/
vim inventory
```

Modify the file to look like this: 

- Command: 

```
cat inventory| grep -v '#' | grep -v '\n'  
```
- Result: 

```
localhost ansible_connection=local ansible_python_interpreter="/usr/bin/env python"

[all:vars]

dockerhub_base=ansible
dockerhub_version=latest

postgres_data_dir=/var/lib/pgawx/docker
host_port=80

docker_compose_dir=/var/lib/awx

pg_username=awx
pg_password=awxpass
pg_database=awx
pg_port=5432

secret_key=awxsecret

awx_official=true

awx_alternate_dns_servers="8.8.8.8,1.1.1.1"

project_data_dir=/var/lib/awx/projects
```

### Execute the playbook: 

```
ansible-playbook -i inventory install.yml -vv
```

### List containers

```
docker container ls
```

### Access AWX through HTTPS

```
https://IP_OF_YOUR_AWX_SERVER
```

- admin / password

Done!

Next steps: 

- Add SSH Keys for passwordless login. 
- Enable WinRM to manage Windows Hosts. 

