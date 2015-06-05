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

## AWS related settings:

  # config.vm.box = "andytson/aws-dummy"
  # config.vm.provider :aws do |aws, override|
  #   aws.access_key_id = ""
  #   aws.secret_access_key = ""
  #   aws.keypair_name = ""
  #   override.ssh.private_key_path = ""
  #   aws.region = "ap-southeast-1"    
  #   aws.instance_type = "t2.small"
  #   aws.security_groups = "default"
  #   aws.ami = "ami-06ccf454"
  #   override.ssh.username = "ubuntu"
  # end

  # config.vm.define "testdb01" do |testdb01|
  #   testdb01.vm.provider "aws" do |vm|
  #   end
  #   testdb01.vm.hostname = ""
  # end  

  config.vm.box = "ubuntu/trusty64"
  config.vm.synced_folder "shared/", "/vagrant", owner: "vagrant", group: "vagrant"

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
