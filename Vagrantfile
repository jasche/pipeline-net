# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|


  config.vm.define "gitlab" do |gitlab|
    gitlab.vm.box = "ubuntu/trusty64"
    gitlab.vm.hostname = 'gitlab'

    gitlab.vm.network :private_network, ip: "192.168.33.11"
    gitlab.vm.network :forwarded_port, guest: 22, host: 10022, id: "ssh"

    gitlab.vm.provision "ansible" do |ansible|
       ansible.verbose = "v"
       ansible.inventory_path="ansible/inventory"
       ansible.playbook = "ansible/gitlab-playbook.yml"
       ansible.sudo = true
    end


    gitlab.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 3070]
    end
  end


  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.box = "ubuntu/trusty64"
    jenkins.vm.hostname = 'jenkins'
#    jenkins.vm.box_url = "ubuntu/trusty64"

    jenkins.vm.network :private_network, ip: "192.168.33.12"
    jenkins.vm.network :forwarded_port, guest: 22, host: 10122, id: "ssh"


    jenkins.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
#      v.customize ["modifyvm", :id, "--name", "jenkins"]
    end
  end

  config.vm.define "nexus" do |nexus|
    nexus.vm.box = "ubuntu/precise64"
    nexus.vm.hostname = 'nexus'
#    nexus.vm.box_url = "ubuntu/precise64"

    nexus.vm.network :private_network, ip: "192.168.33.13"
    nexus.vm.network :forwarded_port, guest: 22, host: 10222, id: "ssh"

    nexus.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "nexus"]
    end
  end
end
