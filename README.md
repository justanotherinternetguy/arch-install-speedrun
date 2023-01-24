# current PB: 4:32:52

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
- Anything is allowed but external tools (running on another system, like SSH or AutoHotkey, `curl`ing an external script, etc)
- YOU ARE ALLOWED to run a `ping google.com` before starting time just to check you have connectivity in the live environment


## Usable% Guide
- in Virtualbox:
- 16000 MB ram
- 6 CPU cores
- 17 gigs of storage

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

`/Par` + `Enter` + `0x` + `:wq`

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
genfstab -U /mnt > /mnt/etc/fstab; arch-chroot /mnt bash -c 'grub-install /dev/sda; grub-mkconfig -o /boot/grub/grub.cfg;systemctl enable NetworkManager;EDITOR=vim visudo;systemctl enable sddm; useradd -mG wheel user;passwd user';reboot
```
## splits

```bash
genfstab -U /mnt > /mnt/etc/fstab; arch-chroot /mnt bash -c 'grub-install
```

```bash
 /dev/sda; grub-mkconfig -o /boot/grub/grub.cfg;systemctl enable NetworkManager;EDITOR=vim visudo;
```

```bash
systemctl enable sddm; useradd -mG wheel user;passwd user';reboot
```

genfstab -U /mnt > /mnt/etc/fstab; arch-chroot /mnt bash -c 'grub-install --target=i386-pc /dev/sda; grub-mkconfig -o /boot/grub/grub.cfg;systemctl enable NetworkManager;EDITOR=vim visudo;systemctl enable sddm; useradd -mG wheel user;passwd user';reboot

- in `visudo` : `/wheel` + `Enter` + `j0xx` + `:wq`
- passwd: `asdf` x2

- After rebooting:
- `asdf`
- firefox + `ctrl` + `l` + `f`
- konsole + `neofetch`

# IN SHORT
`gdisk /dev/sda`

`n` + 3 * `Enter` + `+1M` + `Enter` + `ef02` + `Enter`

`n` + 5 * `Enter`

`w` + `Enter` + `y` + `Enter`

```bash
mkfs.ext4 /dev/sda2
```


```bash
mount /dev/sda2 /mnt
```

```bash
vim /etc/pacman.conf
```

```
TMUX
```

```bash
pacstrap /mnt base linux linux-firmware grub
```

```bash
pacstrap /mnt xorg xorg-xinit neofetch networkmanager firefox xterm
```
```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

```bash
arch-chroot /mnt
```

```bash
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
systemctl enable NetworkManger
passwd a a
```

`reboot`

`xinit`

`neofetch firefox`

![image](https://user-images.githubusercontent.com/96833060/214194483-571c2b6b-14c6-41e8-8301-fae8511a263c.png)

```
gdisk /dev/sda
`n | end sector: +1m | ef02`
`n`
`w`
mkfs.ext4 /dev/sda2
mount /dev/sda2 /mnt
vim /etc/pacman.conf
`/para enter 0x :wq`
tmux
`ctrl b %`
pacman -Sy archlinux-keyring
pacstrap -K /mnt base linux linux-firmware grub
`ctrl b o`
pacstrap /mnt xorg xorg-xinit neofetch networkmanager firefox xterm
`ctrl b o`
genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt
`grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
systemctl enable NetworkManger
passwd a a`
reboot
xinit
neofetch firefox
```


### credit
- https://hackmd.io/@davidak/linux-install-speedrun - for the idea
- https://gist.github.com/MaFeLP/3bd2484299a71ec967630c1155ad8d1f - for the code, my and my friends are working on optimizing it even more
