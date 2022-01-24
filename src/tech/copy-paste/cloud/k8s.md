# Kubernetes useful commands

## Kubectl

### Create secrets

.secrets.txt
```
email=example@example.com
password=secret
```

```bash
kubectl create secret generic "cloudflare-ddns" --from-env-file=./.secrets
```

### Edit live deployment
```shell
kubectl edit deployment <deployment-name>
```

### Quick port forwarding

```shell
kubectl port-forward deployments/<deployment-name> <host-port>:<container-port>
```
