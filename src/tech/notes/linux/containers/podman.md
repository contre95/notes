# Podman

## Getting started

The best way of getting started with Podman, for me, is its website:
[podman.io](http://podman.io).

It also has a handful of [tutorials](https://docs.podman.io/en/latest/Tutorials.html) to get started much quicker if you don't really wanna get into the concepts.


## Rootless podman

These two videos are super useful to understand how podman runs users rootless
and how the different UID and GUID are mapped between [namespaces]().

### Understanding Root Inside and Outside a Container

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/ZgXpWKgQclc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### How User Namespaces Work in Rootless Containers

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/Ac2boGEz2ww" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Here's a list that categorize the known issues and irregularities when running
podman as rootless:

[https://github.com/containers/podman/blob/main/rootless.md](https://github.com/containers/podman/blob/main/rootless.md)


## Generate Unit file for systemd

Once a container/pod is running you can generate an unit file for systemd with the following command:


```bash
podman generate systemd <pod/container-name>  --name 
```

Note: 
* Copying unit files to `/etc/systemd/system` and enabling it marks the unit file to be automatically started at boot. And similarly, copying a unit file to `$HOME/.config/systemd/user` and enabling it marks the unit file to be automatically started on user login.
* As of Podman 4.0, if the pod was craeted with a `pod.yml` and `podman play kube` it's not possible to add the `--new` file to the systemd generated command 
```
Error: cannot use --new on pod "<container-id>": no create command found
```
