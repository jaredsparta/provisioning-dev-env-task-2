# Intro
- This repo will detail how to get MongoDB to run on a VM server

<br>

# Pre-requisites
- Install `Oracle Virtual Box` [here](https://www.virtualbox.org/wiki/Downloads). This is the software that allows us to create virtual machines (VM).

- One will need `Vagrant` installed, find it [here](https://www.vagrantup.com/downloads.html). We use Vagrant to manage our virtual machines in Oracle VM.

- Once `Vagrant` is installed, you need the `vagrant-hostsupdater` plugin. Run `vagrant plugin install vagrant-hostsupdater` to install it. For knowledge, `vagrant plugin uninstall vagrant-hostsupdater` will uninstall this.
> There may be be some problems with this plugin, if you do encounter some just uninstall and then re-install

- One will also need `Ruby` installed, find it [here](https://www.ruby-lang.org/en/downloads/). 

<br>

# Instructions
- To see the tests that we need to pass, go into a terminal and navigate to the directory where you have this repo. Then `cd tests` and run `rake spec`

- To automate the installation of MongoDB into our VM we can make use of a bash script. This can be found in `environment/db/provision.sh`. Bash scripts have the extension `.sh`

- To automatically make MongoDB listen on `0.0.0.0:27017`, we create a `mongod-copy.conf` file in `config-files` and sync this folder with the VM. Within this copy, we change the `port` and `bindip` values. We then use bash commands in `provision.sh` to replace the `mongod.conf` file in `/etc` to this one. The second line allows one to replace the contents of the file without renaming it.
```bash
cd /folder1 
sudo cp -f mongod-copy.conf /etc/mongod.conf
```

- To run the VM, all one would need to then do is navigate to the root of this directory (the level that contains the Vagrantfile) and then `vagrant up`.