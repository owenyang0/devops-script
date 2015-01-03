# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "precise64"

  config.vm.define :master do |master|
    master.vm.network "forwarded_port", guest: 80, host: 8088

    master.vm.hostname = "master"
    master.vm.network "public_network", ip: "192.168.1.141"
  end

  config.vm.define :slave do |slave|
    slave.vm.network "forwarded_port", guest: 80, host: 8089

    slave.vm.hostname = "slave"
    slave.vm.network "public_network", ip: "192.168.1.142"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./ansible-tasks/playbook.yml"
  end
end
