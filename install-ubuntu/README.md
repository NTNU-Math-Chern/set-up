## :octopus: Ubuntu
Instructions can be found [here](https://ubuntu.com/download/desktop#how-to-install) (for latest Ubuntu).
We use [Ubuntu 22.04](https://ubuntu.com/download/alternative-downloads).

- [:octopus: Ubuntu](#octopus-ubuntu)
  - [:teddy\_bear: Prerequisites](#teddy_bear-prerequisites)
  - [:books: Install steps](#books-install-steps)
  - [:nauseated\_face: Potential problems](#nauseated_face-potential-problems)


### :teddy_bear: Prerequisites

- USB

### :books: Install steps
1. download Ubuntu image ([Ubuntu 22.04](https://ubuntu.com/download/alternative-downloads)).
2. create bootable USB flash drive by [balenaEtcher](https://etcher.balena.io/), insert USB
3. boot computer and access BIOS by reptively pressing F2 (or alternatives)
4. boot with Ubuntu installer, follow instructions
5. once successfully installed, restart and remove USB


Update system
```shell
sudo apt update
sudo apt upgrade
```

### :nauseated_face: Potential problems

**Graphic drivers**
If you get a black screen while booting Ubuntu installer, you might need to do the following steps.
During the GRUB boot menu (the screen that says "Try Ubuntu" or "Install Ubuntu"), press 
`e` to edit boot parameters. Add `nomodeset` after `quite splash`:
```sh
linux /casper/vmlinuz ... quiet splash nomodeset
```

After installing Ubuntu, while rebooting after removed USB, you might still occur this problem. Press `shift` (possibly other keys, search for how to access the GRUB menu) after you reboot to access the GRUB menu, repeat the previous step again. Once you are in Ubuntu, open terminal and run
```sh
# sudo apt install vim
sudo vim /etc/default/grub
```
Again, qdd `nomodeset` after `quite splash` and save it for permanent change.
```sh
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```


**Rapid Storage Technology**

(TBD)

**BitLocker**

(TBD)