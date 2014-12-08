# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

# @TODO: Load vhosts dynamically
#require 'yaml'
#vconfig = YAML::load_file("config/vhosts.yml")

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "wheezy64ansible"

  config.vm.box_url = "https://googledrive.com/host/0B0bKMEijMslUY0h2SklTckFiSFU/wheezy64ansible.box"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  config.hostsupdater.aliases = ["example.com", "www.example.com"]

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "www", "/var/www/projects", type: :nfs, map_uid: 0, map_gid: 0

  # Use vagrant-bindfs to re-mount folder
  # config.bindfs.bind_folder "/vagrant-nfs", "/var/www/projects", :owner => "1111", :group => "1111", :'create-as-user' => true, :perms => "u=rwx:g=rwx:o=rwx", :'create-with-perms' => "u=rwx:g=rwx:o=rwx", :'chown-ignore' => true, :'chgrp-ignore' => true, :'chmod-ignore' => true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  #
  config.vm.provider "virtualbox" do |vb|
    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--memory", "768"]
  end

  # Provisioning
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/development.yml"
    ansible.groups = { "vagrant" => ["default"] }
    ansible.sudo = true
    ansible.verbose = "v"
  end
end
