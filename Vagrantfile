# Install required plugins
required_plugins = ["vagrant-hostsupdater"]
required_plugins.each do |plugin|
    exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial"
    config.vm.network "private_network", ip: "192.168.10.150"
    config.hostsupdater.aliases = ["database.local"]
    config.vm.provision "shell", path: "environment/db/provision.sh", privileged: false
    config.vm.synced_folder "config-files", "/folder1"

end