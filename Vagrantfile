# -*- mode: ruby -*-
# vi: set ft=ruby :

##############################################
# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
#
# Be sure to install the Proxy Plugin:
# vagrant plugin install vagrant-proxyconf
#############################################
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Generic setup
  config.vm.box = "danmikita/centos"

  # Forwarding port section

  config.vm.network :forwarded_port, guest: 1521, host: 1521 # Oracle XE
  

  # Making specific setting configuration changes
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "5000"]
    vb.customize ["modifyvm", :id, "--vram", "256"]
  end

  # Using puppet to setup the machine
  config.vm.provision :puppet, run: "always" do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file  = "default.pp"
  # puppet.options = "--verbose --debug"
  end

end
