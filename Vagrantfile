# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # General Vagrant VM configuration.
  config.vm.box = "geerlingguy/debian10"
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provider :virtualbox do |v|
    v.memory = 512
    v.linked_clone = true
  end

  # Load Balancer
  config.vm.define "lb" do |lb|
    lb.vm.hostname = "lvs-lb.test"
    lb.vm.network :private_network, ip: "192.168.60.200"
  end

  # Web Server 1
  config.vm.define "web1" do |web|
    web.vm.hostname = "lvs-web1.test"
    web.vm.network :private_network, ip: "192.168.60.201"
  end

  # Web Server 2         
  config.vm.define "web2" do |web|
    web.vm.hostname = "lvs-web2.test"
    web.vm.network :private_network, ip: "192.168.60.202"
  end

  # Web Server 3         
  config.vm.define "web3" do |web|
    web.vm.hostname = "lvs-web3.test"
    web.vm.network :private_network, ip: "192.168.60.203"
  end

#  config.vm.provision "ansible" do |ansible|
#    ansible.groups = {
#      "load_balancer" => ["lb"],
#      "web_servers"  => ["web1", "web2", "web3"]
#    }
#    ansible.playbook = "configure.yml"
#    ansible.inventory_path = "hosts.ini"
#  end

end
