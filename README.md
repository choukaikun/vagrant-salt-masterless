=======================
vagrant-salt-masterless
=======================

This repo is an example of how to use Salt masterless provisioning with Vagrant.  This setup will pull an OEL 7 box, install Salt, then install nginx.  You can use this VM as a source to package a new Vagrant box for local use since the full vagrant up takes over 3 minutes with the Salt install.  Create the base VM with Salt installed and then use that for further testing.  Here are the steps that worked:

- Install the VM using this Vagrant configuration
  + Make sure the Vagrantfile has the config.ssh.insert_key = false commented out
- Disable salt-minion
  + systemctl stop salt-minion
  + systemctl disable salt-minion
- zero out the disk
  + dd if=/dev/zero of=/EMPTY bs=1M; rm /EMPTY
- Create the Vagrant box
  + vagrant package --base <VM Name> --output <destination file>
    + VM name can be found from vboxmanage list runningvms or vboxmanage list vms
- Add the package to the local Vagrant boxes
  + vagrant box add <box name> <path to the newly created file from the package command>
- Update this Vagrant file using this new box for the config.vm.box = 
- Create your salt state tree in salt/roots
- Go Go Go (vagrant up)
  
