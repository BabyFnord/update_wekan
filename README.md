# update_wekan

[WeKan](https://wekan.github.io) is an open-source kanban board. This script automates updating a bundle-based WeKan instance hosted on Uberspace 7. To install WeKan in the first place, see [this guide](https://lab.uberspace.de/guide_wekan.html).

NOTA BENE
This script is _work in progress_ as WeKan is frequently being updated. Some changes introduced to WeKan became problematic for bundle-installs on U7, this script provides some workarounds for that. One extra feature of the script remains broken for the time being (`--revert`), albeit not a critical one.


## Getting started

### Requirements

A working WeKan instance to be found at `~/wekan/` running as a `supervisord` service, using Node.js 14.21.4, which is a sepcial Node.js version supplied by WeKan as a requirement to run recent versions of WeKan. Node.js 14.21.4 is expected at `~/opt/node14.21.4` (see below for installation instructions if it isn't). Instead of building Node.js `fibers` (which will fail at startup time), `update_wekan` copies `fibers` over from a prior version v6.86 — for your convenience, download the supplied bare v6.86 containing said `fibers` and place it at `~/wekan/`. 

Copy the startup-script `start-wekan.sh` into `$HOME/wekan/`. As a working WeKan instance is a requirement, it is expected that a `wekan.ini` is present at `~/etc/services.d/`.


#### Install Node.js v14.21.4

Copy and paste this line-by-line into your shell:
```bash
VERSION="14.21.4"
```
```bash
SOURCE="https://github.com/wekan/node-v14-esm/releases/download/v14.21.4/node-v14.21.4-linux-x64.tar.gz"
```
```bash
DEST="${HOME}/opt/node${VERSION}"
```
```bash
mkdir --parents "${DEST}"
```
```bash
wget "${SOURCE}"
```
```bash
tar zxvf "node-v${VERSION}-linux-x64.tar.gz"
```
```bash
mv "node-v${VERSION}-linux-x64/"* "${DEST}/"
```
```bash
rm -rf "node-v${VERSION}-linux-x64" "node-v${VERSION}-linux-x64.tar.gz"
```
Now you should have a working copy of Node.js v14.21.4 ready to be used with WeKan >= v7.02.

### Install update_wekan

* Download the current version `update_wekan`, or clone this git and enter the directory:
  ```bash
  git clone https://github.com/BabyFnord/update_wekan.git && cd $(basename $_ .git)
  ```

* Copy the script and make it executable:
  ```bash
  cp update_wekan ~/bin && chmod +x ~/bin/update_wekan
  ```

### Usage

SSH into your Uberspace shell. Type `update_wekan` and relax while the script stops, upgrades and restarts WeKan to the most recent version.

To prevent a failover whenever WeKan introduces new features or dependencies and a new version won't run at first, this script puts each installed version into its own subfolder ($HOME/wekan/wekan-{release version}/)and creates a symlink called `current` to be referenced elsewhere (ie. for [Document Root](https://manual.uberspace.de/web-documentroot/)). So, in case a new WeKan version is troublesome, just run `ln -sfn "$HOME/wekan/wekan-[your prior version no. here]/bundle" "$HOME/wekan/current"` and run `supervisorctl stop wekan && supervisorctl update wekan && supervisorctl start wekan`. 

More information is available by asking the script for help. 
```bash
update_wekan --help
```

## Contribute

The extra feature `--revert` currently needs to be fixed, one of these days. Post your [issues](https://github.com/BabyFnord/uberspace-update_wekan/issues) when you have any, [pull requests](https://github.com/BabyFnord/uberspace-update_wekan/pulls) are welcome.

## Related

### Related Projects

* [uberspace](https://uberspace.de) - Hosting on Asteroids

### Credits

Initially kindly coded by [Kim Diallo](https://diallo.kim), translation and ongoing development by [BabyFnord](https://github.com/BabyFnord). Though abandoned by Kim long ago, I try to maintain and improve the script as good as someone without serious coding skills can.

### Achievements

Tested working since v5.8x. 
