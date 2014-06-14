planeon
===========


Initiate environment 
-
In order to make it easier to clone all required repositories to have an up and running virtual machin with the Plane-Online application with [Jenkins](https://github.com/planeonline/jenkins) as its continues integeration tools, we are using submodules as explaind [here](https://github.com/planeonline/planeon/wiki).

Running following commands will clone all required repositories and their submodules setup & run the required virtual machin using [vagrant](https://github.com/planeonline/vagrant)

``` bash
git clone --recurse-submodules https://github.com/planeonline/planeon.git
cd planeon
git submodule foreach --recursive git checkout master
cd vagrant
cp Vagrantfile_firstrun Vagrantfile
vagrant up --provision
cp Vagrantfile_original Vagrantfile
vagrant reload --no-provision
vagrant ssh
```

Resolving Domains
-
By adding following loopbackes to the host machine's hosts file e.g. /etc/hosts
we will get access to diffeerent services while the virtual machine is running
```
192.168.33.80 service.planeonline.local service.planeonline.local sl.planeonline.local  
192.168.33.80 ci.planeonline.local jenkins.planeonline.local service-layer-ci.planeonline.local sl-ci.planeonline.local s-ci.planeonline.local service-ci.planeonline.local 
192.168.33.80 git.planeonline.local repo.planeonline.loca 
```

Migrate dev environment's database
-
```
cd /projects/www/service-layer/app/
/opt/phinx/bin/phinx migrate
```
