# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|
  # Ansible toolkit
  config.vm.define "tower" do |tower|
    tower.vm.box = "scorputty/centos-awx"
    tower.vm.hostname = "tower.tslab.mx"
    tower.vm.network "private_network", ip: "172.16.8.10"
    tower.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
    tower.vm.provider "virtualbox" do |v|
      v.name = "tower"
      v.memory = 2048
      v.cpus = 2
      # Prevent VirtualBox from interfering with host audio stack
      v.customize ["modifyvm", :id, "--audio", "none"]
      v.customize ["modifyvm", :id, "--graphicscontroller", "vmsvga"]
    end
    
    tower.vm.provision "shell", inline: <<-SHELL
      yum clean all
      yum makecache fast
      yum install -y git curl wget 
    SHELL
  end

  NodeCount = 1

  # test host(s) 
  (1..NodeCount).each do |i|
    config.vm.define "host#{i}" do |host|
      host.vm.box = "centos/7"
      host.vm.hostname = "host#{i}.tslab.mx"
      host.vm.network "private_network", ip: "172.16.8.10#{i}"
      host.vm.provider "virtualbox" do |v|
        v.name = "host#{i}"
        v.memory = 1024
        v.cpus = 1
        # Prevent VirtualBox from interfering with host audio stack
        v.customize ["modifyvm", :id, "--audio", "none"]
        v.customize ["modifyvm", :id, "--graphicscontroller", "vmsvga"]
      end      
    end
  end

end
