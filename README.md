# current PB: 4:02:52

# Rules

## Usable%
- Install official Arch Linux, ISO downloaded from archlinux.org
- CANNOT use `archinstall`
- CANNOT copy/paste (i.e each character must be typed out by hand)
- Virtuabox/VMs are allowed
- After installing, you must open a browser and google something to prove internet connectivity
- Run `neofetch` in your terminal
- Time starts on first keystroke inside of installation environment
- Time ends on `neofetch + Enter` being put into terminal


## Usable% Guide

- Format
```bash
gdisk /dev/sda
```

`n` + 3 * `Enter` + `+1M` + `Enter` + `ef02` + `Enter`

`n` + 5 * `Enter`

`w` + `Enter` + `y` + `Enter`

- Fileystem

```bash
mkfs.ext4 /dev/sda2
```

- Mount

```bash
mount /dev/sda2 /mnt
```

- Parallel downloads, faster

```bash
vim /etc/pacman.conf
```

`/Para` + `Enter` + `0x` + `:wq`

- Open tmux (you can type/get ready other commands as one command runs)

- `ctrl` + `b` + `%` to split panes
- **open THREE PANES**

- `ctrl` + `b` + `o` to switch between panes

- Pane 1
```bash
pacstrap /mnt base linux linux-firmware grub
```

- Pane 2
```bash
pacstrap /mnt xorg-server sddm plasma-meta sudo konsole firefox vim neofetch
```

- Pane 3
```bash
genfstab -U /mnt > /mnt/etc/fstab; arch-chroot /mnt bash -c 'grub-install --target=i386-pc /dev/sda; grub-mkconfig -o /boot/grub/grub.cfg;systemctl enable NetworkManager.service;EDITOR=vim visudo;systemctl enable sddm.service; useradd -mG wheel user;passwd user';reboot
```

- in `visudo` : `/wheel` + `Enter` + `j0xx` + `:wq`
- passwd: `asdf` x2

- After rebooting:
- `asdf`
- firefox + `ctrl` + `l` + `f`
- konsole + `neofetch`
