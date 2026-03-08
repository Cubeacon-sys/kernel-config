# kernel-config
# My Gentoo Kernel Configuration (laptop)
## Kernel Version 
> I am using the 6.18.12-gentoo-x86_64 kernel
## My Features
- I Have AMD Cpu So most intel specific features is disabled
- Stripped down drivers with mostly what i need
- Voluntary Preemptible Kernel
- Tickless Kernel
- Schedutil Governor
- Only Supports ext4 filesystem
- Zram Support (As Module)
- I2C Touchpad Via AMD Gpio Pin support
- Support For Basic Networking like Wifi, ipv4/6 (I don't know about bluetooth i don't use it but it's compiled as module)
- Support for legacy iptables and virtio networking
- Support for virtio drivers
- Support for vhost drivers
- No systemd support
- Support openrc, runit, etc
- Support For gentoo tweaks
- Some tweaks for my AMD cpu
- Compiled for my exact architecture
## Setup & Build
> Make sure to run as Root or just sudo (unless you've set permissions for your user on the /usr/src/linux directory)
0. Make sure your kernel source is symlinked as /usr/src/linux
1. Clone the repository:
``` bash
git clone https://github.com/Cubeacon-sys/kernel-config.git
cd kernel.conf
``` 
2. Copy the Config to the Kernel Source
``` bash
cp .config /usr/src/linux/.config
``` 
3. Build The kernel 
``` bash
make menuconfig # if you want to tweak some stuff
make -j$(nproc)
make modules_install
make install
```
4. Configure the bootloader
> i use grub currently
``` bash
grub-mkconfig -o /boot/grub/grub.cfg
```
## References
Configuring a Custom Linux Kernel (5.6.7-gentoo) It's outdated but that's fine
https://www.youtube.com/watch?v=NVWVHiLx1sU&t=1730s
Making My Touchpad functional
https://forums.gentoo.org/viewtopic-p-8692426.html#8692426

