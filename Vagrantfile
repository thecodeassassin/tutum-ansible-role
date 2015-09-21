# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "jayunit100/centos7"
  config.vm.network :private_network, ip: "192.168.33.39"
#  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "test-ansible-tutum-agent"
    v.memory = 512
    v.cpus = 1
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  # Enable provisioning with Ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "sample-playbook.yml"
  end

end
