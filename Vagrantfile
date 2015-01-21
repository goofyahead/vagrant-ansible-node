# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.define "pub1" do |pub1|
    pub1.vm.box = "ubuntu/trusty64"
    pub1.vm.network "public_network", type: "dhcp", bridge: "eth0"
  end

  config.vm.define "sub1" do |sub1|
    sub1.vm.box = "ubuntu/trusty64"
    sub1.vm.network "public_network", type: "dhcp", bridge: "eth0"
  end

  config.vm.provision :ansible do |ansible|
    ansible.groups = {
        "dev" => ["pub1", "sub1"]
    }
    ansible.verbose = "vvv"
    ansible.playbook = "dev.yml"
    ansible.host_key_checking = false
    config.ssh.forward_agent = true
  end

end
