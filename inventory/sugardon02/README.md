## Run Sugardon02

### Cluster Configs

- kube_proxy_mode: iptables
- kubeconfig_localhost: true
- kube_network_plugin: weave

### Addons

- metallb
- ingress-nginx

```bash
$ ansible-playbook -i inventory/sugardon02/hosts.yaml cluster.yml --become --user=sugardon_admin --private-key=./.ssh/id_rsa -vvv
```

## Setup Ingress Service

Create Ingress Service

```bash
$ kubectl apply -f inventory/sugardon02/ingress-nginx-service.yaml
```

## Setup tekton pipeline

Install tekton pipeline

https://github.com/tektoncd/pipeline/blob/master/docs/install.md#installing-tekton-pipelines-on-kubernetes

```bash
$ kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
```
