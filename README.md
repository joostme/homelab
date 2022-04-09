# K8S at Home :sailboat:

Heavily inspired by [k3s-gitops](https://github.com/cbirkenbeul/k3s-gitops). Thanks a lot!

## Installation

Create `flux-system` namespace
````sh
kubectl create ns flux-system
```

Add SOPS secret
```sh
cat ~/sops/age/keys.txt |
    kubectl -n flux-system create secret generic sops-age \
    --from-file=age.agekey=/dev/stdin
```

Install Flux
```sh
kubectl apply -k ./cluster/base/flux-system
```
