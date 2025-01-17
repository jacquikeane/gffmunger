# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/xenial64"

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
  # config.vm.network "forwarded_port", guest: 80,   host: 8080, host_ip: "127.0.0.1"

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
  
  config.vm.synced_folder ".",                     "/home/vagrant/GFFMunger"
#   # CONDA BUILDS:  if you want to use this VM for conda builds,
#   # uncomment next line & tweak path to your bioconda-receipies repo
#   config.vm.synced_folder "../bioconda-recipes",   "/home/vagrant/bioconda-recipes"
  
  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    # vb.gui = true
  
    # Customize the amount of memory on the VM:
    vb.memory = "8192"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
   apt-get update -qq
   apt-get install -y genometools
   apt-get install -y git python3 python-setuptools python3-biopython python3-pip
   pip3 install dumper gffutils
   pip3 install --upgrade pip
   grep GENOMETOOLS_PATH /home/vagrant/.bashrc || echo 'export GENOMETOOLS_PATH="/usr/bin/gt"' >> /home/vagrant/.bashrc
#    ###   CONDA BUILDS:  if you want to use this VM for conda builds, uncomment following block
#    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
#    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
#    apt-get update -qq
#    apt-get install --yes docker-ce
#    usermod -aG docker vagrant   
#    curl -o /usr/local/bin/circleci https://circle-downloads.s3.amazonaws.com/releases/build_agent_wrapper/circleci && \
#       chmod +x /usr/local/bin/circleci
#    curl -o /usr/local/bin/miniconda https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
#       chmod +x /usr/local/bin/miniconda && \
#       echo " **************************************************************************************" && \
#       echo " *  To finish conda install, log in and run                                           *" && \
#       echo " *    bash /usr/local/bin/miniconda && source ~/.bashrc && conda install conda-build  *" && \
#       echo " **************************************************************************************"
#    ### end of CONDA BUILDS block
  SHELL
end

