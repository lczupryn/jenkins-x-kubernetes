# BWCE Application

For manual helm installation update in values.yaml
```YAML
...
image:
  repository: draft
  tag: dev
...
```
and run:
```
helm install --install --name <name> .  --set ingress.host=<url> --namespace=<namespace>
```
