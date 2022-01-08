# Docker oneliners

Remove all existing containers

```bash
docker container rm -f $( docker container ls  -aq)
```

Same for volumes 

```bash
docker volume rm $(docker volume ls)
```

Same for images

```bash
docker image rm -f $(docker image ls -aq)
```
