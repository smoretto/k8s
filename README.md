# Kubernetes

## Metrics server
Version: **v0.4.2**
```
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.4.2/components.yaml
```

## MetalLB
Version: **v0.9.6**

Create `metallb/config/secret.key` with MetalLB secret.

```
kubectl apply -k metallb
```

## Traefik
Version: **v2.4.8**

```
kubectl apply -k traefik
```

## Cert Manager
Version: **v1.0.3**

```
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.3.0/cert-manager.yaml
```

## External DNS
Version: **v0.7.6**

```
kubectl apply -k external-dns
```