# Ceph Squid v19.x on Ubuntu 24.04 — 3-Node Cluster

Complete hands-on guide for deploying a production-style Ceph Squid cluster on three Ubuntu 24.04 nodes with cephadm, Podman, 3 MONs, 3 MGRs, 3 OSDs, and the Ceph Dashboard.

## Lab topology

| Host | Private IP | Role | OS disk | Ceph OSD disk |
|---|---|---|---|---|
| ceph1 | 10.109.244.7 | Bootstrap, MON, MGR, OSD | /dev/vda ~93G | /dev/vdb 100G |
| ceph2 | 10.109.244.8 | MON, MGR, OSD | /dev/vda ~93G | /dev/vdb 100G |
| ceph3 | 10.109.244.9 | MON, MGR, OSD | /dev/vda ~93G | /dev/vdb 100G |

Public addresses are used only for administration/dashboard access; Ceph cluster traffic uses the private 10.109.244.0/23 network.

## Result

- Ceph Squid 19.x
- 3-node MON quorum
- 1 active + 2 standby MGRs
- 3 OSDs using the dedicated 100G `/dev/vdb` disks
- `HEALTH_OK`
- Ceph Dashboard enabled

## Documentation

- `01-introduction/Day-1-Ceph-Introduction.md`
- `02-cluster-setup/Day-2-Prerequisites-and-Node-Setup.md`
- `02-cluster-setup/Day-3-Cephadm-Bootstrap.md`
- `02-cluster-setup/Day-4-Add-Monitors-Managers-OSDs.md`
- `03-dashboard-access/Day-5-Dashboard-NGINX-LetsEncrypt.md`
- `04-validation/Day-6-Validation-and-Troubleshooting.md`
- `05-next-step-kubevirt/README.md`
- `COMMAND-REFERENCE.md`

## Safety

Never commit Ceph dashboard passwords, private SSH keys, keyrings, or other credentials to Git. Use placeholders in documentation.

## Next phase

The next integration is Ceph RBD → Ceph-CSI → Kubernetes StorageClass/PVC → KubeVirt VM with a Ceph-backed disk.
