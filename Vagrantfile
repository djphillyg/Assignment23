# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box="ubuntu/xenial64"
  #provision file with permission
  config.vm.provision "file", source: "~/.ssh/pbh_key.pem", destination: "/home/ubuntu/.ssh/pbh_key.pem"
  config.vm.provision "file", source: "./lamp/ansible.cfg", destination: "~/.ansible.cfg"
  config.vm.provision "file", source: "./lamp", destination: "/home/ubuntu/"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "lamp/main.yml"
    ansible.verbose = true
    ansible.install = true
    ansible.limit = "all"
    ansible.inventory_path = "lamp/roles/inventory"
  end
end
