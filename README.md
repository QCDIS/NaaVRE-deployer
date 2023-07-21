# NaaVRE deployer

## Usage

- Copy `inventories/sample.yaml` to `inventories/my_cluster.yaml` and edit it.
- Run `ansible-playbook -i inventories/my_cluster.yaml install.yaml`


## Steps

- Install basic system dependencies [dependencies/install.yaml](dependencies/install.yaml):
  - docker
  - container runtime interface (containerd)
  - kubelet, kubeadm, kubectl
- Install basic k8s cluster [k8s-base/install.yaml](k8s-base/install.yaml):
  - configure firewall
  - setup master node
  - enroll worker nodes
  - container network interface (Flannel)
- Install k8s extras [k8s-extras/install.yaml](k8s-extras/install.yaml):
  - persistent volume provisioner (NFS)
    - dashboard
    - ingress controller (ingress-nginx)
