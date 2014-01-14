# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "base"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # configure a persistent storage for mysql data
  config.persistent_storage.enabled = true
  config.persistent_storage.location = '/persistent-storage/virtualdrive.vdi'
  config.persistent_storage.size = 5000
  config.persistent_storage.mountname = 'mysql'
  config.persistent_storage.filesystem = 'ext4'
  config.persistent_storage.mountpoint = '/var/lib/mysql'
  config.persistent_storage.volgroupname = 'myvolgroup'

  # Shell script provisioning
  config.vm.provision :shell, :path => "install.sh"

  config.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777", "fmode=666"]
end
