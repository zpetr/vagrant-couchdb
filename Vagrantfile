# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	#config.vm.box = "hashicorp/precise64"
	#config.vm.box = "debian-73-x64-virtualbox-puppet"
	#config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/debian-73-x64-virtualbox-puppet.box"
	
	config.vm.box = "centos-6.5-64-puppet"
	config.vm.box_url = "https://vagrantcloud.com/puppetlabs/boxes/centos-6.5-64-puppet/versions/3/providers/virtualbox.box"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

	config.vm.network "private_network", ip: "10.0.0.101"
  
	config.vm.provider :virtualbox do |v|
		v.customize ["modifyvm", :id, '--chipset', 'ich9'] # solves kernel panic issue on some host machines
		v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
		v.customize ["modifyvm", :id, "--memory", 2048]
		v.customize ["modifyvm", :id, "--ioapic", "on"]
		#v.gui = true # turn gui on
	end

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Enable provisioning with Puppet stand alone.  Puppet manifests
  # are contained in a directory path relative to this Vagrantfile.
  # You will need to create the manifests directory and a manifest in
  # the file default.pp in the manifests_path directory.
  #
  
	# Update puppet version
	#config.vm.provision :shell, :path => "scripts/bootstrap_puppet.sh"
  
	# Get some puppet modules
	#config.vm.provision :shell, :path => "scripts/bootstrap_puppet_modules.sh"
	
	
	config.vm.provision "puppet" do |puppet|
		puppet.manifests_path = "puppet/manifests"
		puppet.manifest_file  = "init.pp"
		#puppet.options="--verbose --debug"
	end
end
