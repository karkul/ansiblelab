# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true
  # Ansible toolkit
  config.vm.define "tower" do |tower|
    tower.vm.box = "scorputty/centos-awx"
    tower.vm.hostname = "tower.tslab.mx"
    tower.vm.network "private_network", ip: "172.16.8.10"
    tower.hostmanager.aliases = %w(tower.tslab.mx tower)
    tower.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
    tower.vm.network "forwarded_port", guest: 3000, host: 3000, host_ip: "127.0.0.1"
    tower.vm.network "forwarded_port", guest: 2200, host: 2202, host_ip: "127.0.0.1"
    tower.vm.provider "virtualbox" do |v|
      v.name = "tower"
      v.memory = 2048
      v.cpus = 2
      # Prevent VirtualBox from interfering with host audio stack
      v.customize ["modifyvm", :id, "--audio", "none"]
      v.customize ["modifyvm", :id, "--graphicscontroller", "vmsvga"]
    end

    ## Adding my own SSH keys
    #tower.ssh.insert_key = false
    #tower.ssh.private_key_path = ['files/id_rsa', '~/.ssh/id_rsa']
    #tower.vm.provision "file", source: "files/id_rsa.pub", destination: "~/.ssh/authorized_keys"  
    
    tower.vm.provision "shell", inline: <<-SHELL
      yum clean all
      yum makecache fast
      yum install -y git curl wget 
      yum update -y ansible
    SHELL
  end

  NodeCount = 1

  # Test host(s) 
  (1..NodeCount).each do |i|
    config.vm.define "host#{i}" do |host|
      host.vm.box = "centos/7"
      host.vm.hostname = "host#{i}.tslab.mx"
      host.vm.network "private_network", ip: "172.16.8.10#{i}"
      host.hostmanager.aliases = %w("host#{i}.tslab.mx" "host#{i}")
      host.vm.provider "virtualbox" do |v|
        v.name = "host#{i}"
        v.memory = 1024
        v.cpus = 1
        # Prevent VirtualBox from interfering with host audio stack
        v.customize ["modifyvm", :id, "--audio", "none"]
        v.customize ["modifyvm", :id, "--graphicscontroller", "vmsvga"]
      end
    
      ## Adding my own SSH keys
      #host.ssh.insert_key = false    
      #host.vm.provision "file", source: "files/id_rsa.pub", destination: "~/.ssh/authorized_keys"        
    end
  end

end
