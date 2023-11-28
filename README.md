# NaaVRE deployer

## Usage

- Copy `inventories/sample.yaml` to `inventories/my_cluster.yaml` and edit it.
- Run `ansible-playbook -i inventories/my_cluster.yaml install.yaml`


## Steps

- Install basic system dependencies [dependencies/install.yaml](dependencies/install_all.yaml):
  - configure firewall
  - container runtime interface (containerd)
  - kubelet, kubeadm, kubectl
  - helm
  - configure system for k8s
- Install basic k8s cluster [k8s-base/install.yaml](k8s-base/install_all.yaml):
  - setup master nodes
  - enroll worker nodes
  - container network interface (Flannel)
- Install k8s extras [k8s-extras/install.yaml](k8s-extras/install_all.yaml):
  - persistent volume provisioner (NFS)
  - dashboard
  - ingress controller (ingress-nginx)
