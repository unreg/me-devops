# me-devops
Preconfigured lxd-container with a local k8s-environment

Features:
* Funtoo-based lxd-container
* k3s as Kubernetes
* k9s - terminal based UI to interact with your Kubernetes
* helm and kubectl
* Portainer
* container registry
* manifest examples for PostgreSQl, RabbitMQ and Hasura

Install:
```sh
wget https://github.com/unreg/me-devops/releases/download/2022.10.19/k3s-lxd-x86_64-me-devops.tar.xz
```

```sh
lxc import k3s-lxd-x86_64-me-devops.tar.xz --alias me-devops
lxc init me-devops me-devops
lxc config device add "me-devops" "kmsg"  unix-char source="/dev/kmsg" path="/dev/kmsg"
lxc start me-devops
```

Go inside a container:
```sh
lxc exec me-devops -- su --login dev /home/dev/mpx.sh
```

Uninstall and remove:
```sh
lxc stop me-devops
lxc rm me-devops
lxc image rm me-devops
```

