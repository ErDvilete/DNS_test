# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  config.vm.define "tierra" do |tierra|
    tierra.vm.network "private_network", ip: "192.168.57.103"
    tierra.vm.provision "shell", inline: <<-SHELL
      apt-get update -y
      apt-get install -y bind9 bind9-dnsutils
    SHELL
    tierra.vm.provision "shell", name: "master-dns" , inline: <<-SHELL

    SHELL
  end


  config.vm.define "venus" do |venus|
    venus.vm.network "private_network" , ip: "192.168.57.102"
    venus.vm.provision "shell",name : "slave", inline:  <<-SHELL

    SHELL
  end
end
