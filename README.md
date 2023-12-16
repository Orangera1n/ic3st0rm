<h1 align="center">SSH Ramdisk Script</h1>
<p align="center">
  <a href="https://github.com/Orangera1n/ic3st0rm/graphs/contributors" target="_blank">
    <img src="https://img.shields.io/github/contributors/Orangera1n/ic3st0rm.svg" alt="Contributors">
  </a>
  <a href="https://github.com/Orangera1n/ic3st0rm/commits/main" target="_blank">
    <img src="https://img.shields.io/github/commit-activity/w/Orangera1n/ic3st0rm.svg" alt="Commits">
  </a>
</p>

<p align="center">
Create and boot a SSH ramdisk on checkm8 devices
</p>

---

# Prerequsites

1. A computer running macOS/linux
2. A checkm8 device (A7-A11)

# Usage

1. Clone and cd into this repository: `git clone https://github.com/Orangera1n/ic3st0rm --recursive && cd ic3st0rm`
    - If you have cloned this before, run `cd ic3st0rm && git pull` to pull new changes
2. Run `./ic3st0rm.sh <iOS version for ramdisk>`, **without** the `<>`.
    - The iOS version doesn't have to be the version you're currently on, but it should be close enough, and SEP has to be compatible
    - If you're on Linux, you will not be able to make a ramdisk for 16.1+, please use something lower instead, like 16.0
        - This is due to ramdisks switching to APFS over HFS+, and another dmg library would have to be used
3. Place your device into DFU mode
    - A11 users, go to recovery first, then DFU.
4. Run `./ic3st0rm.sh boot` to boot the ramdisk
5. Run `./ic3st0rm.sh ssh` to connect to SSH on your device
6. Finally, to mount the filesystems, run `mount_filesystems`  
    - /var is mounted to /mnt2 in the ssh session.
    - /private/preboot is mounted to /mnt6.
    - DO NOT RUN THIS IF THE DEVICE IS ON A REALLY OLD VERSION OR THE DEVICE IS ON IOS 16.4+
7. Have fun!

# Linux notes

On Linux, usbmuxd will have to be restarted. On most distros, it's as simple as these 2 commands in another terminal:
```
sudo systemctl stop usbmuxd
sudo usbmuxd -p -f
```

# Other commands

- Reboot your device: `./ic3st0rm.sh reboot`
- Erase all data from your device: `./ic3st0rm.sh reset`
- Dump onboard SHSH blobs: `./ic3st0rm.sh dump-blobs`
- Delete old SSH ramdisk: `./ic3st0rm.sh clean`

# Other Stuff

# Credits

- [tihmstar](https://github.com/tihmstar) for pzb/original iBoot64Patcher/img4tool
- [xerub](https://github.com/xerub) for img4lib and restored_external in the ramdisk
- [Cryptic](https://github.com/Cryptiiiic) for iBoot64Patcher fork
- [opa334](https://github.com/opa334) for TrollStore
- [Nebula](https://github.com/itsnebulalol) for a bunch of QOL fixes to this script
- [OpenAI](https://chat.openai.com/chat) for converting [kerneldiff](https://github.com/mcg29/kerneldiff) into [C](https://github.com/Orangera1n/kerneldiff_C)
- [Ploosh](https://github.com/plooshi) for KPlooshFinder
