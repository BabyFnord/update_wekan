# update_wekan

[WeKan](https://wekan.github.io) is an open-source kanban board. This script automates updating a bundle-based WeKan instance hosted on Uberspace 7. To install WeKan in the first place, see [this guide](https://lab.uberspace.de/guide_wekan.html).

NOTA BENE
This script is _work in progress_ as WeKan is frequently being updated. Some changes introduced to WeKan became problematic for bundle-installs on U7, this script provides some workarounds for that. Some extra features of the script currently are broken, I'll fix them when I have the time and knowledge to do so. 

It _might_ happen that WeKan introduces new features or dependencies and a new version won't run at first, needs some fixes to the startup-script or whatever 🤷🏻‍♂️. To prevent a failover, this script puts each installed version into its own subfolder ($HOME/wekan/wekan-{release version}/)and creates a symlink called `current` to be referenced elsewhere (ie. for [Document Root](https://manual.uberspace.de/web-documentroot/)). If needed, stop Wekan by typing `tmux attach` and when `tmux` shows the running script, press `CTRL+b`then `d`. A next step could be to revert the symlink to your preferred previous version, and run the startup-script again. 

## Getting started

### Requirements

A working WeKan instance to be found at `~/wekan/` and working Node.js 14.21.4. The latter is an unofficial Node.js version, which you need to install (see below for instructions), furthermore, Node.js 14.21.3 and .4 are unsupported (as in EOL) on Uberspace 7. Hence, you need to manually install that: The workaround is to put Node.js 14.21.4 at `~/opt/node14.21.4` and instead of building `fibers` (which will fail at startup time), and to copy the required Node `fibers` from a previous version v6.86 into the downloaded WeKan folder. The fibers version will be provided at a later stage …

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

SSH into your Uberspace shell. Type `update_wekan`, the script will ask for your permission to stop a running WeKan instance initiated by tmux (any prior WeKan instance would have to be initiated using 'tmux new -s wekan ~/wekan/start-wekan.sh'). After this step, `update_wekan` does the fiddly update process automagically. Finally, the script asks whether it should start your new WeKan version in a new `tmux` session. To leave that session gracefully, type `CTRL-b` then `d` to return to the shell—WeKan is up and running the most recent version.

More information available by asking the script for help, but please remember for the time being, unfortunately any extra feature outside of a standard update process is non-functional:
```bash
update_wekan --help
```

## Contribute

In its current state, the script does _not_ provide its prior extra features beyond its main job—which is automating the update procedure. Inactive code exists for those extra features, waiting to be fixed one of these days. Post your [issues](https://github.com/BabyFnord/uberspace-update_wekan/issues) when you have any, [pull requests](https://github.com/BabyFnord/uberspace-update_wekan/pulls) are welcome.

## Related

### Related Projects

* [uberspace](https://uberspace.de) - Hosting on Asteroids

### Credits

Initially kindly coded by [Kim Diallo](https://diallo.kim), though abandoned long ago.
Translation and ongoing development by [BabyFnord](https://github.com/BabyFnord)

### Achievements

Tested working since v5.8x. 
