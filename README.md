# tjth-pihole

Docker deployment for pihole

# Kubernetes deployment

Kubernetes deployment is achieved using Helm and the following commands.

NOTE: This project requires the following tools to be installed on the cluster:

* Longhorn for persistent storage
* MetalLB for load balancing
* Sealed Secrets for secret management

```
cd helm
```

The below command can be used to write a new web password to the secrets.yaml file (replace secrets.yaml as required).

```
kubectl create secret generic pihole-web-password --from-literal=password=<password> --dry-run=client -o yaml | 
kubeseal \
      --controller-name=sealed-secrets \
      --controller-namespace=default \
      --namespace pihole \
      --format yaml > secrets.yaml
```

Finally, use the following command to deploy the chart.

```
helm install pihole .
```

