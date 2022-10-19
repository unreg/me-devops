# me-devops
Preconfigured image lxd-container with a local k8s-environment

### Features:
* image of a Funtoo-based lxd-container
* k3s as Kubernetes
* k9s - terminal based UI to interact with your Kubernetes
* helm and kubectl
* Portainer
* container registry
* manifest examples for PostgreSQl, RabbitMQ and Hasura

### Prerequisities
* LXC/LXD on host system
* Docker in host system (optional)
* free disk 5 Gb or more

### Install

Get image:
```sh
wget https://github.com/unreg/me-devops/releases/download/2022.10.19/k3s-lxd-x86_64-me-devops.tar.xz
```
Install image and init container:
```sh
lxc import k3s-lxd-x86_64-me-devops.tar.xz --alias me-devops
lxc init me-devops me-devops
lxc config device add "me-devops" "kmsg"  unix-char source="/dev/kmsg" path="/dev/kmsg"
lxc start me-devops
```

### Use

Go inside a container:
```sh
lxc exec me-devops -- su --login dev /home/dev/mpx.sh
```

### Uninstall

Uninstall container and remove image
```sh
lxc stop me-devops
lxc rm me-devops
lxc image rm me-devops
```

