# kvc-wireguard-kmod

This is a [kmods-via-containers](https://github.com/kmods-via-containers/kmods-via-containers) implementation for WireGuard using [atomic-wireguard](https://github.com/jdoss/atomic-wireguard.git) example.

The intended utility of this repository is for fulfilling some of the Openshift encrypt cluster traffic steps here: https://docs.projectcalico.org/security/encrypt-cluster-pod-traffic#install-wireguard


## Quick config variables guide


|[wireguard-kmod.conf](wireguard-kmod.conf)|comment|
|---|---|
|WIREGUARD_KERNEL_VERSION| Run `uname -r` on your cluster to fill out this field |
|WIREGUARD_VERSION| Please obtain the `tar.xz` file of the latest [wireguard-linux-compat version here](https://git.zx2c4.com/wireguard-linux-compat/) without the 'v' prefix |
|WIREGUARD_SHA256| SHA256 of the above `wireguard-linux-compat-(version).tar.xz` file |
|KERNEL_CORE_RPM| Link to kernel-core rpm for the selected kernel version. See Note 1 below |
|KERNEL_DEVEL_RPM| Link to kernel-core rpm for the selected kernel version. Note 1 below |
|KERNEL_MODULES_RPM| Link to kernel-core rpm for the selected kernel version. See Note 1 below |


#### Note 1: You can find links to  official packages in your [RedHat Subscription](https://access.redhat.com/downloads/content/package-browser). Links must be accessible by your cluster.


## Compatibility table

WireGuard snapshots vs kernel version compatibility for [atomic-wireguard](https://github.com/projectcalico/) kvc build system

This may aid in populating the [wireguard-kmod.conf](wireguard-kmod.conf). However, please always use the [latest wireguard snapshot](https://git.zx2c4.com/wireguard-linux-compat/) vs the latest kernel version (by running `uname -r` on your cluster).

| WIREGUARD_VERSION | WIREGUARD_SHA256 | WIREGUARD_KERNEL_VERSION |
|---|---|---|
| 1.0.20210219 | 99d35296b8d847a0d4db97a4dda96b464311a6354e75fe0bef6e7c4578690f00 | 4.18.0-240.15.1.el8_3.x86_64 |
| 1.0.20200520 | 16e7ae4bef734b243428eea07f3b3c3d4721880c3ea8eb8f98628fd6ae5b77c3 | 4.18.0-193.28.1.el8_2.x86_64 |