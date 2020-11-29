# Intro

- This repo will detail how to get MongoDB to run on a VM server

- We also configure it to listen on `0.0.0.0:27017`

<br>

# Pre-requisites
- Install `Oracle Virtual Box` [here](https://www.virtualbox.org/wiki/Downloads). This is the software that allows us to create virtual machines (VM).

- Install `Vagrant` [here](https://www.vagrantup.com/downloads.html). We use Vagrant to manage our virtual machines in Oracle VM.

- Once `Vagrant` is installed, you need the `vagrant-hostsupdater` plugin. 
> Run `vagrant plugin install vagrant-hostsupdater` to install it

> Run `vagrant plugin uninstall vagrant-hostsupdater` to uninstall it

> There may be be some problems with this plugin, if you do encounter some just uninstall and then re-install

- One will also need `Ruby` installed, find it [here](https://www.ruby-lang.org/en/downloads/). 


<br>

# Instructions
- To see the tests that we need to pass, go into a terminal and navigate to the directory where you have this repo. Then `cd tests` and run `rake spec`

<br>

- To automate the installation of MongoDB into our VM we can make use of a bash script. This can be found in `environment/db/provision.sh`. 
> Bash scripts have the extension `.sh`

<br>

- Since we want the database to listen on `0.0.0.0:27017` we must change the configuration file found in `/etc/mongod.conf`. We can do this through our provision file
> The command we add is `sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/' /etc/mongod.conf` which will change the bindIp as shown

<br>

- To run the VM, all one would need to then do is navigate to the root of this directory (the level that contains the Vagrantfile) and then `vagrant up`.

<br>

- Finally, when running the tests, we will see that all have passed

