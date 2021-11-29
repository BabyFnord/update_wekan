# update_wekan

Easily update existing wekan installations on Uberspace 7 spaces.

## About

Wekan is an open-source kanban board which allows a card-based task and to-do management. This script is intended to make it easier to keep an existing instance up to date.

## Getting started

### Requirements

A working wekan instance. -  To install Wekan in the first place, see [this guide](https://lab.uberspace.de/guide_wekan.html) for instructions.

### Get update_wekan

* Download the latest version from the [release page](https://github.com/BabyFnord/uberspace-update_wekan/releases) and unzip it or clone this git and enter the directory:

  ```bash
  git clone https://github.com/BabyFnord/uberspace-update_wekan.git && cd $(basename $_ .git)
  ```

* Copy the script and make it executable

  ```bash
  cp update_wekan ~/bin && chmod +x ~/bin/update_wekan
  ```

### Usage

To download, build and switch to latest wekan version just run the script

```bash
update_wekan
```

For more information on usage, just ask the script itself

```bash
update_wekan --help
```

#### Features

The main function of this script is to download, install and test the latest wekan version to an uberspace account, and then
upgrade the running instance to the latest version.

The currently supported options:

1. `--debug`
Make the output verbose.

1. `--reinstall`
Remove folder of current lattest wekan if present and perform a fresh clean install

1. `--revert [version]`
Roll back to choosen wekan version if related folder is presend. If called without
specifc version, the penultimate one is put back into operation.

1. `--help`
Print usage information

#### Automation

***Keep in mind that this script is still new and maybe not that stable—
if you decide to automate updates, check your logs***

To fully automate the process, let it run by crond. For example, to update every night
at 3:15 a.m., add this to your crontab:

```bash
# Perform wekan updates automagically with https://github.com/BabyFnord/uberspace-update_wekan
15 03 * * * $HOME/bin/update_wekan
```

Help to the crontab syntax can be found on [crontab.guru](https://crontab.guru/) for a different setting.

## Contribute

Constructive [issues](https://github.com/BabyFnord/uberspace-update_wekan/issues) and [pull requests](https://github.com/BabyFnord/uberspace-update_wekan/pulls) are welcome.

## Related

### Related Projects

* [wekan](https://wekan.github.io) - What it is all about
* [uberspace](https://uberspace.de) - Hosting on Asteroids
* [crontab.guru](https://crontab.guru/) - mentioned as an aid
* [markdownlint](https://github.com/markdownlint/markdownlint) - lint what you are reading

### Credits

Coded by [Kim Diallo](https://diallo.kim)

Translation, maintenance and testing by [BabyFnord](https://github.com/BabyFnord)

### Achievements

update_wekan worked fine with Wekan v5.17 > v5.27 > v5.28. Currently, upgrading from wekan v5.28 onwards requires just a few extra steps (as documented in https://github.com/BabyFnord/update_wekan/issues/4#issuecomment-980735972).
