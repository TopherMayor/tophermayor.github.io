---
layout: post
title: Proxmox 8 PCI Passthrough
date: 2024-07-18 15:47 -0700
categories: [Homelab, Proxmox]
tags: [proxmox, github, documentation, hookscripts, virtual machines, homelab]
---




## Setup

Bootloader: Grub\
Graphics Card: AMD Radeon 5700xt 

## Working Configuration

Edit/create grub file located at ```/etc/default/grub``` 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet amd_iommu=on iommu=pt nomodeset pcie_acs_override=downstream initcall_blacklist=sysfb_init"
``` 

Edit/create modules file located at ```/etc/modules```
```
vendor-reset
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
```

Edit/create vfio.conf file located at ```/etc/modprobe.d/vfio.conf```

```
options vfio-pci ids=1002:731f,1002:ab38 disable_vga=1
```

Created a service to set the reset_method using method shown [here](https://github.com/gnif/vendor-reset/issues/46)


Edit/create vrwa service file located at ``` /lib/systemd/system/vrwa.service```

```
[Unit]
Description=vrwa Service
After=multi-user.target

[Service]
ExecStart=/usr/bin/bash -c 'echo device_specific > /sys/bus/pci/devices/0000:0c:00.0/reset_method'

[Install]
WantedBy=multi-user.target
```

Once created run the following command to enable to service:
 
```
systemctl enable vrwa
```


***
## Resources

* [https://pve.proxmox.com/wiki/PCI_Passthrough](https://pve.proxmox.com/wiki/PCI_Passthrough)
* [https://forum.proxmox.com/threads/amd-gpu-inaccessible-after-vm-poweroff-unable-to-change-power-state-from-d3cold-to-d0-device-inaccessible.130975/#post-633195](https://forum.proxmox.com/threads/amd-gpu-inaccessible-after-vm-poweroff-unable-to-change-power-state-from-d3cold-to-d0-device-inaccessible.130975/#post-633195)
* [https://github.com/gnif/vendor-reset](https://github.com/gnif/vendor-reset)
* [https://forum.proxmox.com/threads/problem-with-gpu-passthrough.55918/page-2#post-478351](https://forum.proxmox.com/threads/problem-with-gpu-passthrough.55918/page-2#post-478351)
* [https://forum.proxmox.com/threads/gpu-passthrough-issues-after-upgrade-to-7-2.109051/](https://forum.proxmox.com/threads/gpu-passthrough-issues-after-upgrade-to-7-2.109051/)
* [https://www.reddit.com/r/homelab/comments/b5xpua/the_ultimate_beginners_guide_to_gpu_passthrough/](https://www.reddit.com/r/homelab/comments/b5xpua/the_ultimate_beginners_guide_to_gpu_passthrough/)
