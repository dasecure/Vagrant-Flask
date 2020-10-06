# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  # config.vm.hostname = "RestAPI"
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  # config.vm.network "private_network", ip:"192.168.88.8"

  # config.vm.synced_folder "../data", "/vagrant_data"

  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  #   vb.cpus = 2
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get upgrade -y
    apt-get install -y python3-pip
    pip3 install flask
    cp /vagrant/app.py ~/
    cd ~
    export FLASK_APP=app.py
    flask run -h 0.0.0.0
  SHELL
end
