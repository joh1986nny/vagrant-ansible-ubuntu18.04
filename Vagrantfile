# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

#Cambiar Configuración Regional
ENV["LC_ALL"] = "en_US.UTF-8"

Vagrant.configure("2") do |config|

  #Configuracion Virtual Machine
  config.vm.define "Ubuntu18.04" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-18.04" #imagen
    ubuntu.vm.hostname = "UbuntuVagrant" #hostname
    ubuntu.vm.network 'private_network', ip: '192.168.200.20'
    ubuntu.vm.boot_timeout = 360 # Apagado si error de arranque en 6 mins

    #SSH
    ubuntu.vm.network "forwarded_port", guest: 22, host:2222, id: "ssh", auto_correct: true

    #Use Apache
    ubuntu.vm.network "forwarded_port", guest: 80, host:8081, id: "apache", auto_correct: true
 
    #ANSIBLE
    ubuntu.vm.provision "ansible", run: "always" do |ansible|
      ansible.verbose = 'vvv'
      ansible.inventory_path = "ansible/entorno/inventory"
      ansible.playbook = "ansible/playbook.yml" 
    end

  end #ubuntu 

 #Provider
 config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    #vb.gui = true
    
    # Customize the VM:
    vb.memory = "2048"
    vb.name = "Ubuntu18.04-Vagrant"
 end #provider

end #vagrant


    # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL