# RBAC

## Create service account and role for CI

```
kubectl apply -f service-account.yaml

SECRET=$(kubectl get sa ci-deploy-dev -n kube-system -o 'jsonpath={.secrets[0].name}')
CA=$(kubectl get secret $SECRET -n kube-system -o 'jsonpath={.data.ca\.crt}')
TOKEN=$(kubectl get secret $SECRET -n kube-system -o 'jsonpath={.data.token}'|base64 -d)
URL=https://k8s.unseen.it:6443

kubectl config --kubeconfig=config-dev.yaml set clusters.dev-cluster.server $URL
kubectl config --kubeconfig=config-dev.yaml set clusters.dev-cluster.certificate-authority-data $CA
kubectl config --kubeconfig=config-dev.yaml set users.dev-user.token $TOKEN --set-raw-bytes=true
kubectl config --kubeconfig=config-dev.yaml set contexts.dev-context.cluster dev-cluster
kubectl config --kubeconfig=config-dev.yaml set contexts.dev-context.user dev-user
kubectl config --kubeconfig=config-dev.yaml set current-context dev-context
```
