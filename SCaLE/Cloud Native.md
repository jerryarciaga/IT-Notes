# [Kubernetes and the Dragons in Linux Kernel vs. Userspace Tools](https://www.socallinuxexpo.org/scale/22x/presentations/kubernetes-and-dragons-linux-kernel-vs-userspace-tools)
[Jussi Nummelin](https://www.socallinuxexpo.org/scale/22x/speakers/jussi-nummelin)
## Outline
* Dragons?
* Kernal vs userspace
## Kernelspace vs userspace
* `iptables` configure netfilter rules
* `netfilter` Kernel networking framework, Packet filtering, NAT
## `iptables`
* Can manage different "backends"
* Used by many k8s components
* Pre-containers era tools
## Ensure all components use same mode
* Kube-proxy talking legacy but host FW Nftables
* K8s community has common wrapper tooling to detect the mode
	* https://github.com/kubernetes-sigs/iptables-wrappers
## Ensure all components use same versions of `iptables`

## `modprobe`
* Userspace tool to (un)load kernel modules
* Handles dependencies
* Interacts with kernel