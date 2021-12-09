# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|

    NM = 1
	(1..NM).each do |machine_id|
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
		end
	end

    NW = 0
	(1..NW).each do |machine_id|
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
		end
	end
end
