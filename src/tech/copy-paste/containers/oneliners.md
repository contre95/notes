# Containers


---
## Podman 

### Run command on the same Namespace as your containers

This command is usefull when you want to re-define permission on rootless podman containers or to debug permissions in general.

```shell
podman unshare <command>
```

### Run a k8s Pod manifest with Podman

```shell
podman play kube pod.yml 
```
Killing the same pod:
```shell
podman play kube --down pod.yml
```
---

## Docker

### Forcefully remove every `<container/image>`

```bash
docker container rm -f $(docker <container/image> ls -aq)
```

### Forcefully remove every `<volume/network>`

```bash
docker container rm -f $(docker <volume/network> ls -aq)
```
