### check sha iso
- echo "fa95fb748b34d470a7cfa5e3c1c8fa1163e2dc340cd5a60f7ece9dc963ecdf88 \
*ubuntu-21.04-desktop-amd64.iso" | shasum -a 256 --check

### update grub
- fedora, sudo grub2-mkconfig -o /boot/grub2/grub.cfg
- ubuntu, sudo grub-mkconfig -o /boot/grub/grub.cfg
- update, sudo update-grub

### fail boot, just grub interface
- grub> set pager=1
- grub> ls
- find boot file
- grub> ls (hd0,3)
- grub> ls (hd0,2)/
- grub> ls (hd0,2)/boot
- grub> set root=(hd0,2)
- grub> linux /boot/vmlinuz-5.3.18-lp152.57-default root=/dev/sda2
- grub> initrd /boot/initrd-5.3.18-lp152.57-default
- grub> boot






