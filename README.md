## ZFS PKGBUILDs for  Arch Linux with sane defaults
### Usage
#### Build newest tagged release with latest default kernel package - this is default
```sh
cd user
makepkg -sCr
cd ../kernel
makepkg -sCr
cd .. && ls */*-linux-ARCH-*
```
#### Build last commit from current release branch with linux-lts kernel
```sh
cd user
makepkg -sCr _buildtype=branch _branch=7.0-release
cd ../kernel
makepkg -sCr _buildtype=branch _branch=7.0-release _kernelname=-lts
cd .. && ls */*-linux-lts-git-*
```
#### Build 0.7.1 tag with linux-zen 4.13.4-1 kernel
```sh
cd user
makepkg -sCr _buildtype=tag _tag=0.7.1
cd ../kernel
makepkg -sCr _buildtype=tag _tag=0.7.1 _kpkgver=4.13.4-1 _kernelname=-zen
cd .. && ls */*-linux-zen-*
```
#### Build exact ZFS revision against SPL HEAD  with newest linux-hardened kernel
```sh
cd user
makepkg -sCr _buildtype=commit _splcommit=origin/HEAD _zfscommit=some.rev.id.
cd ../kernel
makepkg -sCr _buildtype=commit _splcommit=origin/HEAD _zfscommit=some.rev.id. _kernelname=-hardened
cd .. && ls */*-linux-hardened-git-*
```

### Available Variables
```
_branch
_buildtype
_kernelname
_kpkgver
_splcommit
_tag
_zfscommit
```

### FAQ
#### What the pkg 4.13.7.1.0.7.2.0.7.1.13.1 version string contains?
* 4.13.7.1 = built against kernel pkg 4.13.7-1 , `-` replaced with `.`
* 0.7.2 = the nearest ZFS tag in the past that is reachable on current branch from checkout. `zfs-` prefix striped.
* 0.7.1 = the nearest SPL tag in the past that is reachable on current branch from checkout. `spl-` prefix striped.
* 13 = Number of commits in ZFS since zfs-0.7.2 tag
* 1 = Number of commits in SPL since spl-0.7.1 tag

### Licenses
* The license of ZFS is CDDL.
* The license of SPL is GPLv2.
