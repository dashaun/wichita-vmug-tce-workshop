## Photon OS

- Download the [Photon OS](https://github.com/vmware/photon) OVA 
  - [https://github.com/vmware/photon]
- Deploy the OVA (VSphere or Workstation) - 4vCPU & 16GB RAM & 51GB of disk
- Install [Tanzu CLI](https://tanzucommunityedition.io/docs/v0.10/cli-installation/)
  - [https://tanzucommunityedition.io/docs/v0.10/cli-installation/]
- Install Docker

Notes:
- Here is how to expand the disk on the VM after it is deployed:
  https://vmware.github.io/photon/assets/files/html/3.0/photon_troubleshoot/expanding-disk-partition.html
---

## Using VMware Workstation 16 Pro

VMware Workstation 16 Pro [30 Day Evaluation](https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html)

- "Open a Virtual Machine"
- Read and accept the terms of the license agreement.
- Edit virtual machine settings:
- 16GB Ram, 4x 1-core CPU, 16GB disk
  - 18 GB of swap on the host really helped 

---

## Start and Login

- root -- changeme
- Update root password

---

## Start docker

```bash
systemctl start docker
systemctl enable docker
docker info
# Install other tools - make sure network can reach outside
tdnf install sudo parted nano wget tar -y
```

---

## Regular user instead of root
```bash
useradd -m -G sudo dashaun
usermod -aG docker dashaun
passwd dashaun
su - dashaun
```

---
