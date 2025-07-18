# NaaVRE deployer

## Usage

- Copy `inventories/sample-k8s.yaml` to `inventories/my_cluster.yaml` and edit it.
- Run `ansible-playbook -i inventories/my_cluster.yaml install.yaml`


## Steps

- Install basic system dependencies [dependencies/all.yaml](dependencies/all.yaml):
  - configure firewall
  - container runtime interface (containerd)
  - kubelet, kubeadm, kubectl
  - helm
  - configure system for k8s
- Install basic k8s cluster [k8s-base/install.yaml](k8s-base/install_all.yaml):
  - setup master nodes
  - enroll worker nodes
  - container network interface (Flannel)
- Install k8s extras [k8s-extras/all.yaml](k8s-extras/all.yaml):
  - cert-manager
  - ingress controller (ingress-nginx)
  - NFS persistent volume provisioner
  - install the csi-s3 driver and storage class. Variables
    - `create_minio_pvs` - If true, run the playbook 
    - `minio_storage_class` - The name of the storage class to be created
    - `navre_rw_access_key` - The access key for the MinIO bucket
    - `navre_rw_secret_key` - The secret key for the MinIO bucket
    - `minio_endpoint` - The endpoint for the MinIO service
    - `minio_region` - The region for the MinIO service
  - create static PV for the MinIO buckets. Variables
    -  `pvc_namespace`  - The namespace where the PVCs will be created. For example, if we deploy a lab in the `naavre-labs` namespace, this should be set to `naavre-labs`.
    - `create_minio_pvs` - If true, run the playbook 
    - `minio_storage_class` - The name of the storage class created in the previous step
    - `bucket_name` - The name of the bucket to use for the static PV
    - `pvc_access_mode` - The access mode for the PVC. For the `naa-vre-public` bucket, this should be set to `ReadOnlyMany`. For the `naa-vre-user-data` bucket, this should be set to `ReadWriteMany`.
    
