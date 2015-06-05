# encoding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

current_dir    = File.dirname(File.expand_path(__FILE__))
configs        = YAML.load_file("#{current_dir}/config.yaml")
vagrant_config = configs['configs']

Vagrant.require_version ">= 1.7.0"
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = true
  config.vm.synced_folder "shared/", "/vagrant", owner: "vagrant", group: "vagrant"
  #config.vm.hostname = ".informagerealty.com"
  #config.vm.box_url = "/home/administrator/Documents/Softwares/ubuntu-14.04.2-server-amd64.iso"
  #config.vm.network "forwarded_port", guest: 80, host: 80, auto_correct: true
  # config.vm.provision :shell, :path => "bootstrap.sh"
  # config.vm.provider "virtualbox" do |vb|
  #   vb.customize ["modifyvm", :id, "--memory", "512"]
  # end

  config.vm.define "web01" do |web01|
    web01.vm.provider "virtualbox" do |vm|
      vm.name = "web01"
      vm.memory = 512
    end
    web01.vm.network :private_network, ip: "192.168.56.101"
    web01.vm.hostname = "web01." + vagrant_config['domain_name']
  end

  config.vm.define "search01" do |search01|
    search01.vm.provider "virtualbox" do |vm|
      vm.name = "search01"
      vm.memory = 512
    end
    search01.vm.network :private_network, ip: "192.168.56.102"
    search01.vm.hostname = "search01." + vagrant_config['domain_name']
  end

  config.vm.define "db01" do |db01|
    db01.vm.provider "virtualbox" do |vm|
      vm.name = "db01"
      vm.memory = 512
    end
    db01.vm.network :private_network, ip: "192.168.56.103"
    db01.vm.hostname = "db01." + vagrant_config['domain_name']
  end

end
