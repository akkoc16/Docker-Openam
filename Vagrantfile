# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"
  config.vm.hostname = "docker.local"
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  config.vm.network "private_network", ip: "192.168.100.10"
  config.vm.network "public_network", use_dhcp_assigned_default_route: true
  
  
  #config.vm.synced_folder ".", "/vagrant_data"
  config.vm.synced_folder ".", "/vagrantfiles", type: "rsync",
  rsync__exclude: ".git/"
 
    
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  vb.memory = 2048
  vb.cpus = 2
  vb.name = "Centos-7-Docker"

#  config.vm.provision "shell", inline: <<-SHELL
  #yum update -y
  #yum install deltarpm
  #yum install -y git
  #yum install -y vim
  #yum install -y bind-utils
  #yum install -y net-tools
  #yum install -y tmux
  #yum install -y bash-completion
  #yum install -y ansible
  #yum install -y httpd
 
#SHELL
# use pip to install ansible required version for ARA
# Run Ansible from the Vagrant VM
     config.vm.provision "ansible_local" do |ansible|
     ansible.playbook = "playbook.yml"
#     ansible.install_mode = "pip"
#     ansible.version = "2.5.14"
     ansible.inventory_path = "inventory"
     ansible.verbose = true
     ansible.limit= "all"
     end
end
end
