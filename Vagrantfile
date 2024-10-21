# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update -y
    apt-get install -y bind9 bind9-dnsutils
  SHELL

  config.vm.define "tierra" do |tierra|
    tierra.vm.network "private_network", ip: "192.168.57.103"
    tierra.vm.provision "shell", name: "master-dns", inline: <<-SHELL
      cp -v /vagrant/named.conf.options /etc/bind/named.conf.options
      cp -v /vagrant/named /etc/default/named
      cp -v /vagrant/tierra/named.conf.local /etc/bind/named.conf.local
      cp -v /vagrant/db.sistema.test.dns /var/lib/bind
      cp -v /vagrant/db.sistema.test.rev /var/lib/bind
    SHELL
  end


  config.vm.define "venus" do |venus|
    venus.vm.network "private_network" , ip: "192.168.57.102"
    venus.vm.provision "shell", name: "slave", inline: <<-SHELL
      cp -v /vagrant/named /etc/default/named
      cp -v /vagrant/named.conf.options /etc/bind/named.conf.options
      cp -v /vagrant/venus/named.conf.local /etc/bind/named.conf.local
      cp -v /vagrant/db.sistema.test.dns /var/lib/bind
      cp -v /vagrant/db.sistema.test.rev /var/lib/bind
    SHELL
  end
end
