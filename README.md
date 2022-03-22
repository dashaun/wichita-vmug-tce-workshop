# Wichita VMUG - Tanzu Community Edition Workshop - March 2022

## Getting Started

1.  Download the [Photon OS](https://github.com/vmware/photon) OVA
2.  Deploy the OVA (VSphere or Workstation) - 4vCPU & 16GB RAM & 51GB of disk
3.  Install [Tanzu CLI](https://tanzucommunityedition.io/docs/v0.10/cli-installation/)
4.  Install Docker - Need cgroup version 1 (see below)

```bash
$ docker info | grep -i cgroup
Cgroup Driver: cgroupfs
Cgroup Version: 1
```
> Cgroup Version 2 will not work at this time
