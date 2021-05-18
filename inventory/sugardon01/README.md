## Run Create Cluster

```bash
$ ANSIBLE_CONFIG=inventory/sugardon01/ansible.cfg ansible-playbook -i inventory/sugardon01/hosts.yaml cluster.yml --become --user=sugardon_admin --private-key=./.ssh/id_rsa -vvv
```

## Config

ref. 
https://medium.com/@leonardo.bueno/setting-up-a-kubernetes-cluster-with-kubespray-1bf4ce8ccd73

### ./group_vars/k8s_cluster/k8s-cluster.yml

```bash
# Make a copy of kubeconfig on the host that runs Ansible in {{ inventory_dir }}/artifacts
# kubeconfig_localhost: false
kubeconfig_localhost: true

# Set your docker version
# https://github.com/kubernetes-sigs/kubespray/blob/master/docs/vars.md#common-vars-that-are-used-in-kubespray
# version detail : https://github.com/kubernetes-sigs/kubespray/blob/master/roles/container-engine/docker/vars/ubuntu.yml
docker_version: "20.10"
```

### ./group_vars/k8s_cluster/k8s-net-calico.yml

```bash
calico_iptables_backend: "NFT"

# For Sakura VPS Local
calico_ip_auto_method: "interface=ens4"
```

### ./group_vars/all/all.yml
```bash
## Internal loadbalancers for apiservers
loadbalancer_apiserver_localhost: true
# valid options are "nginx" or "haproxy"
loadbalancer_apiserver_type: nginx  # valid values "nginx" or "haproxy"
```

