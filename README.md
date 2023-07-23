# update_wekan

[WeKan](https://wekan.github.io) is an open-source kanban board. This script automates updating a bundle-based WeKan instance hosted on Uberspace 7. To install WeKan in the first place, see [this guide](https://lab.uberspace.de/guide_wekan.html).

NOTA BENE
This script is _work in progress_ and WeKan is frequently being updated. Some introduced changes to WeKan were quite problematic when run as a bundle-install on U7, the script now provides workarounds for a robust instance. Some previous features of the script are broken, I'll fix them when I have the time and knowledge to do so. 

Be aware it _might_ happen that a new version won't run at first, needs some fixes to the startup-script or whatever 🤷🏻‍♂️. Preventing a failover, the script puts each installed version into its own subfolder and creates a symlink `current` to be referenced elsewhere (ie. for [Document Root](https://manual.uberspace.de/web-documentroot/)). If a new version won't run, you can simply revert the symlink to a previous version, and run the startup-script again. Use at your own risk. Yet is is unlikely any harm would be done to an existing installation. 

## Getting started

### Requirements

A working WeKan instance to be found at `~/wekan/` and working Node.js 14.21.3. The latter is unsupported (EOL) on Uberspace 7, you need to manually install it. The workaround is to put Node.js 14.21.3 at `~/opt/node14.21.3` and instead of building `fibers` (which will fail at startup time), and to copy the required Node `fibers` from a previous version v6.86 into the downloaded WeKan folder. The fibers version will be provided at a later stage …

### Get update_wekan

* Download the latest version from the [release page](https://github.com/BabyFnord/update_wekan/releases), unzip it or clone this git and enter the directory:
  ```bash
  git clone https://github.com/BabyFnord/update_wekan.git && cd $(basename $_ .git)
  ```

* Copy the script and make it executable:
  ```bash
  cp update_wekan ~/bin && chmod +x ~/bin/update_wekan
  ```

### Usage

SSH into your Uberspace shell. Stop the current WeKan instance by typing `tmux attach`, choose `wekan` and stop the process by pressing `CTRL-B` then `D`. Now run the script in order to download, build and switch over to the latest WeKan version:
```bash
update_wekan
```
Run 'tmux new -s wekan ~/wekan/start-wekan3.sh' to start WeKan.

More information available by asking the script for help:
```bash
update_wekan --help
```

#### Features

Available options:
1. `--debug` _NOT WORKING RELIABLY AT PRESENT_
Print debugging information to stdout.

1. `--reinstall` _NOT WORKING RELIABLY AT PRESENT_
Remove the current wekan if present, and perform a fresh install.

1. `--revert [version]` _NOT WORKING RELIABLY AT PRESENT_
Roll back to given wekan version, if the specified folder exists.
If called without specifc version, the penultimate is put back into operation.

1. `--help`
Print this help text.


## Contribute

In its current state, the script is a hack and does _not_ provide reliable features beyond the update procedure. Some broken and inactive code exists, waiting to be fixed. Post your [issues](https://github.com/BabyFnord/uberspace-update_wekan/issues) and [pull requests](https://github.com/BabyFnord/uberspace-update_wekan/pulls) are welcome.

## Related

### Related Projects

* [uberspace](https://uberspace.de) - Hosting on Asteroids

### Credits

Initially kindly coded by [Kim Diallo](https://diallo.kim), though abandoned long ago.
Translation and ongoing development by [BabyFnord](https://github.com/BabyFnord)

### Achievements

Tested working since v5.8x. 
