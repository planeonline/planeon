planeon
===========


Initiate environment 
-
In order to make it easier to clone all required repositories to have an up and running virtual machin with the Plane-Online application with [Jenkins](https://github.com/planeonline/jenkins) as its continues integeration tools, we are using submodules as explaind [here](https://github.com/planeonline/planeon/wiki).

Running following commands will clone all required repositories and their submodules setup & run the required virtual machin using [vagrant](https://github.com/planeonline/vagrant)

``` bash
git clone --recurse-submodules git@github.com:planeonline/planeon.git
cd planeon
git submodule foreach --recursive git checkout master
cd vagrant
cp Vagrantfile_firstrun Vagrantfile
vagrant up --provision
cp Vagrantfile_original Vagrantfile
vagrant reload --no-provision
vagrant ssh
```

Migrate dev environment's database
-
```
cd /projects/www/service-layer/app/
/opt/phinx/bin/phinx migrate
```
