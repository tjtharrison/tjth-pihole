# tjth-pihole
Docker deployment for pihole

# Kubernetes deployment

First, install namespaces:

```commandline
kubectl apply -f namespaces.yaml
```

Then, create secrets:

```commandline
kubectl create secret generic pihole-web-password --from-literal=password=<password> --namespace pihole
```

Finally, deploy the manifests:

```commandline
kubectl apply -f pihole.yaml
```


pihole-FTL sqlite3 /etc/pihole/pihole-FTL.db "VACUUM INTO 'pihole-FTL.backup.db'"