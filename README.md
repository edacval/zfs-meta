## ZFS PKGBUILDs for  Arch Linux with sane defaults
### Usage
#### Build newest tagged release with latest default Arch kernel package - this is default
```sh
cd user
makepkg -sCr
cd ../kernel
makepkg -sCr
cd .. && ls */*-linux-ARCH-*
```
#### Build exact ZFS commit with newest linux-lts kernel
```sh
cd user-git
makepkg -sCr _zfsrev=some.rev.id.
cd ../kernel-git
makepkg -sCr _zfsrev=some.rev.id. _kernelname=-lts
cd .. && ls */zfs-linux-lts-git-*
```
#### Build ZFS zfs-0.8.1 tag with linux-zen 5.2.14.zen1 kernel
```sh
cd user-git
makepkg -sCr _zfsrev=zfs-0.8.1
cd ../kernel-git
makepkg -sCr _zfsrev=zfs-0.8.1 _kernelname=-zen _kpkgver=5.2.14.zen1
cd .. && ls */zfs-linux-zen-git-*
```
### Available Variables
```
_kernelname
_kpkgver
_zfsrev
```

### FAQ
#### What the pkg 5.13.7.1.0.8.2.13 version string contains?
* 5.13.7.1 = built against kernel pkg 5.13.7-1 , `-` replaced with `.`
* 0.8.2 = the nearest ZFS tag in the past that is reachable on current branch from checkout, `zfs-` prefix striped.
* 13 = Number of commits in ZFS since zfs-0.8.2 tag

### Licenses
* The license of ZFS is CDDL.
* The license of SPL is GPLv2.
