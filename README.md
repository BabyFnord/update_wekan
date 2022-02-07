# update_wekan

[WeKan](https://wekan.github.io) is an open-source kanban board. This script automates updates of installations hosted on Uberspace 7.

## Getting started

### Requirements

A working WeKan instance. To install WeKan in the first place, see [this guide](https://lab.uberspace.de/guide_wekan.html).

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

Run the script (via SSH in your Uberspace shell) in order to download, build and switch over to the latest WeKan version:
```bash
update_wekan
```

More information available by asking the script for help:
```bash
update_wekan --help
```

#### Features

Available options:
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

***If you decide to automate updates, check your logs in case of inconsistencies!***

Automatic updates can be set up with crond. Example: To run the script every night at 3:15 am, add this to your crontab:
```bash
# Perform WeKan updates automagically with https://github.com/BabyFnord/update_wekan
15 03 * * * $HOME/bin/update_wekan
```

Read more about crontab options at [crontab.guru](https://crontab.guru/).

## Contribute

Constructive [issues](https://github.com/BabyFnord/uberspace-update_wekan/issues) and [pull requests](https://github.com/BabyFnord/uberspace-update_wekan/pulls) are welcome.

## Related

### Related Projects

* [uberspace](https://uberspace.de) - Hosting on Asteroids
* [crontab.guru](https://crontab.guru/) - mentioned as an aid
* [markdownlint](https://github.com/markdownlint/markdownlint) - lint what you are reading

### Credits

Initially kindly coded by [Kim Diallo](https://diallo.kim).
Translation and ongoing development by [BabyFnord](https://github.com/BabyFnord)

### Achievements

Tested working since v5.8x, including latest WeKan v6.03.
