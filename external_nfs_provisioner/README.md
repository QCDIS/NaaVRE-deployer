# External NFS provisioner

Use these playbooks to deploy k8s with a NFS provisioner on an external cluster.

- Run the usual k8s deployment playbooks, skipping [k8s-extras/nfs_provisioner.yaml](../k8s-extras/nfs_provisioner.yaml)
- Create an inventory from [inventories/sample-nfs.yaml](../inventories/sample-nfs.yaml)
- If the NFS server's firewall has never been configured, run [external_nfs_provisioner/firewall_reset.yaml](../external_nfs_provisioner/firewall_reset.yaml)
- Run [external_nfs_provisioner/all.yaml](../external_nfs_provisioner/all.yaml)
