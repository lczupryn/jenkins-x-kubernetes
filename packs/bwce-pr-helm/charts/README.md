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

// promote through all 'Auto' promotion Environments
//sh "jx promote -b --all-auto --timeout 1h --version \$(cat ../../VERSION)"
sh "echo \"bwceapp200.jx-staging.\$(kubectl get svc --all-namespaces -o jsonpath=\'{range .items[?(@.spec.type==\"LoadBalancer\")]}{.status.loadBalancer.ingress[0].ip}\').nip.io \" > BWCEAPPURL"
sh "helm install --install --name bwceapp200 .  --set ingress.host=\$(cat BWCEAPPURL) --namespace=jx-staging"

}
