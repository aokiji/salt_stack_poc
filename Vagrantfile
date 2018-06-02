# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.1"

  # network
  config.vm.network "private_network", ip: "192.168.33.10"

  # synced folders
  config.vm.synced_folder "provision/salt/", "/srv/salt/"
  config.vm.synced_folder "provision/pillar/", "/srv/pillar"

  # fix dependencies for salt
  config.vm.provision "shell", inline: <<-SHELL
    sudo yum install -y python2
  SHELL

  # provision
  config.vm.provision :salt do |salt|
    salt.masterless = true
    salt.minion_config = "provision/etc/minion"
    salt.run_highstate = true
    salt.verbose = true
  end
end
