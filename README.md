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

## Install docker-compose

```
apt install python-pip
pip install docker-compose
```

## 
