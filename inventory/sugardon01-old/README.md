## Run

Create Cluster

CentOS8
- https://github.com/kubernetes-sigs/kubespray/issues/5726
- https://github.com/kubernetes-sigs/kubespray/blob/master/docs/centos8.md

addons  

- metallb
- ingress-nginx
- Local volume provisioner

```bash
$ ANSIBLE_CONFIG=inventory/sugardon01-old/ansible.cfg ansible-playbook -i inventory/sugardon01/hosts.yaml cluster.yml --become --user=sugardon_admin --private-key=./.ssh/id_rsa -vvv
```

## Setup Ingress Service

Create Ingress Service

```bash
$ kubectl apply -f inventory/sugardon01/ingress-nginx-service.yaml 
```

## Setup tekton pipeline

Install tekton pipeline

https://github.com/tektoncd/pipeline/blob/master/docs/install.md#installing-tekton-pipelines-on-kubernetes

```bash
$ kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
```
