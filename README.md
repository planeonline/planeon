planeon
===========


Initiate environment 
-
``` bash
git clone --recurse-submodules git@github.com:planeonline/planeon.git
cd planeon
git submodule foreach --recursive git checkout master
cd vagrant;
cp Vagrantfile_firstrun Vagrantfile
vagrant up --provision;
cp Vagrantfile_original Vagrantfile
vagrant reload --no-provision;
vagrant ssh;
```
