# uberspace-update_wekan
Facilitates (ie. eases) updates of existing Wekan installations on Uberspace 7 hosted domains. 

Wekan is an open-source kanban board which allows a card-based task and to-do management. Visit https://wekan.github.io for an in-depth overview. To install Wekan in the first place, see https://lab.uberspace.de/guide_wekan.html for instructions.

Usage:
update_wekan [options]
--debug							Print various debugging information to stdout.
--reinstall					Remove folder of current latest wekan if present, and perform a fresh install
--revert [version]	Roll back to given wekan version, if specified folder exists. If called without specifc version, the penultimate is put back into operation.
--help							Print this help text and exit.
