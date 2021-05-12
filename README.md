uberspace-update_wekan
======================
Facilitates (*ie. eases*) updates of existing Wekan installations on Uberspace 7 hosted domains. 

Wekan is an open-source kanban board which allows a card-based task and to-do management. Visit https://wekan.github.io for an in-depth overview. To install Wekan in the first place, see https://lab.uberspace.de/guide_wekan.html for instructions. Kindly coded by Kim Diallo at uberspace.de. Translation, minor text updates and testing provided by BabyFnord. Currently tested working with Wekan v5.27 > v5.28 …

Usage
-----
update_wekan [options]  
    --debug		Print various debugging information to stdout.  
    --reinstall					Remove folder of current latest wekan if present, and perform a fresh install.  
    --revert [version]	Roll back to given wekan version, if specified folder exists. If called without specifc version, the penultimate is put back into operation.  
    --help							Print this help text and exit.  

To update an existing installation, put this script into *~/bin* and make it executable (chmod +x ~/bin/update_wekan). Run *update_wekan* and wait for the script to complete. 
