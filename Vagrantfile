# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # General Vagrant VM configuration.
  config.vm.box = "centos/8"
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: "true"
  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.linked_clone = true
    v.cpus = 2
  end

  # Staking node.
  config.vm.define "test" do |app|
    app.vm.hostname = "test.test"
    app.vm.network :private_network, ip: "192.168.60.5"
  end
  
  # Provisioning configuration for Ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision.yml"
  end
end
