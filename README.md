# update_wekan

[Wekan](https://wekan.github.io) is an open-source kanban board. This script automates installations hosted on Uberspace 7.

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
Print debugging information to stdout.

1. `--reinstall`
Remove the current wekan if present, and perform a fresh install.

1. `--revert [version]`
Roll back to given wekan version, if the specified folder exists.
If called without specifc version, the penultimate is put back into operation.

1. `--help`
Print this help text.

#### Automation

***If you decide to automate updates, be sure to check your logs in case of inconsistencies!***

Automatic updates can set up with crond. 
Example: To run the script every night at 3:15 am, add this to your crontab:

```bash
# Perform wekan updates automagically with https://github.com/BabyFnord/update_wekan
15 03 * * * $HOME/bin/update_wekan
```

Read more about crontab options here [crontab.guru](https://crontab.guru/).

## Contribute

Constructive [issues](https://github.com/BabyFnord/uberspace-update_wekan/issues) and [pull requests](https://github.com/BabyFnord/uberspace-update_wekan/pulls) are welcome.

## Related

### Related Projects

* [wekan](https://wekan.github.io) - What it is all about
* [uberspace](https://uberspace.de) - Hosting on Asteroids
* [crontab.guru](https://crontab.guru/) - mentioned as an aid
* [markdownlint](https://github.com/markdownlint/markdownlint) - lint what you are reading

### Credits

Coded by [Kim Diallo](https://diallo.kim).
Translation, fixes and testing by [BabyFnord](https://github.com/BabyFnord)

### Achievements

Confirmed working, tested by upgrading from wekan-v5.82 → 5.83.
