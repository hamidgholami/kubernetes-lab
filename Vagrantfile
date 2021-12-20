# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|

    MASTER = 1
	(1..MASTER).each do |machine_id|
		config.vm.define "master-11.#{20+machine_id}" do |machine|
			machine.ssh.insert_key = false
			machine.vm.box = "generic/ubuntu2004"
			machine.vm.hostname = "master-#{20+machine_id}"
			machine.vm.network :private_network , 
				:ip =>  "192.168.11.#{20+machine_id}", 
				:libvirt__forward_mode => "route",
				:libvirt__dhcp_enabled => false
            
			config.vm.provider "libvirt" do |v|
				v.storage :file, :size => '1G'
				v.storage :file, :size => '1G'
				v.storage :file, :size => '1G'
				v.memory = 2048
				v.cpus = 2
				#v.storage_pool_name = 'pool_myhome_SSD'
		    end
			# Synced Directories
			config.vm.synced_folder '.', '/vagrant', type: 'rsync', disabled: true
			config.vm.synced_folder '.', '/vagrant', disabled: true
			config.vm.synced_folder './provision', '/vagrant/provision', type: 'rsync'
			# Provision
			config.vm.provision 'shell', path: "./provision/bootstrap.sh"
		end
	end

    WORKER = 1
	(1..WORKER).each do |machine_id|
		config.vm.define "worker-11.#{30+machine_id}" do |machine|
			machine.ssh.insert_key = false
			machine.vm.box = "generic/ubuntu2004"
			machine.vm.hostname = "worker-#{30+machine_id}"
			machine.vm.network :private_network , 
				:ip =>  "192.168.11.#{30+machine_id}", 
				:libvirt__forward_mode => "route",
				:libvirt__dhcp_enabled => false
            
			config.vm.provider "libvirt" do |v|
				v.storage :file, :size => '1G'
				v.storage :file, :size => '1G'
				v.storage :file, :size => '1G'
				v.memory = 2048
				v.cpus = 2
				#v.storage_pool_name = 'pool_myhome_SSD'
		    end
			# Synced Directories
			config.vm.synced_folder '.', '/vagrant', type: 'rsync', disabled: true
			config.vm.synced_folder '.', '/vagrant', disabled: true
			config.vm.synced_folder './provision', '/vagrant/provision', type: 'rsync'
			# Provision
			config.vm.provision 'shell', path: "./provision/bootstrap.sh"
		end
	end
end
