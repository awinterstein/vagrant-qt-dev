# -*- mode: ruby -*-
# vi: set ft=ruby :

# Workaround for changed server URL. Can be removed when using vagrant 2.x.
Vagrant::DEFAULT_SERVER_URL.replace('https://vagrantcloud.com')

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "cerritus/kubuntu-lts"
  config.vm.box_version = "1.2.0"

  config.vm.synced_folder "src/", "/home/vagrant/src/",
    owner: "vagrant", group: "vagrant"

  config.ssh.forward_agent = true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    vb.name = "Qt Development"

    # Display the VirtualBox GUI when booting the machine
    vb.gui = true

    # Enable USB 2.0
    vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["modifyvm", :id, "--usbehci", "on"]

    # # Customize the amount of memory on the VM:
    # vb.memory = "1024"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Run Ansible to install Git into the VM (for using Ansible Galaxy later on)
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "bootstrap.yml"
  end

  # Run Ansible from wthin the Vagrant VM
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.galaxy_role_file = "requirements.yml"
  end
end
