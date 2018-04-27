# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "main" do |main|

    # Prepare a box more secure than the default base box.
    # Generally, the base box conforms to following requirements:
    #   https://www.vagrantup.com/docs/boxes/base.html
    main.vm.box = "ubuntu/xenial64"

    # In case if you want to bind vm's ssh port to host...
    # Note that you generally not need this since host <-> guest
    # private address is available.
    #
    # main.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2322

    # portforwarding 3035
    # main.vm.network "forwarded_port", guest: 3035, host: 3035

    # host <-> guests network private IP.
    main.vm.network "private_network", ip: "192.168.33.10"

    # In case a bridge connection is wanted,
    # so that the VM is connected to LAN where host resides.
    # main.vm.network "public_network"

    # Use the original ssh key.
    # main.ssh.private_key_path = "../my_private_key"

    # Change the permission of default mount folder.
    main.vm.synced_folder ".", "/vagrant", mount_options: ["dmode=700,fmode=600"]

    main.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
    end

    main.ssh.forward_x11 = true
    main.ssh.forward_agent = true
  end
end
