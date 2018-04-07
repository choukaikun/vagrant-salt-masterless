# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ol7-latest"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.synced_folder "salt/roots/", "/srv/"

#  config.ssh.insert_key = false # Use this when making a VM for packaging

  config.vm.provision :salt do |salt|
    salt.minion_config = "salt/minion"
    salt.run_highstate = true
    salt.colorize = true
    salt.verbose = true
  end

end
