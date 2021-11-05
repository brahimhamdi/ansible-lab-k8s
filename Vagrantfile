Vagrant.configure("2") do |config|  
#  config.vm.provider "virtualbox"
  config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "generic/ubuntu2004"
    ansible.vm.hostname = "ansible"
    ansible.vm.network :private_network, ip: "192.168.201.10"
  end

  config.vm.define "node1" do |node1|
    node1.vm.box = "generic/ubuntu2004"
    node1.vm.hostname = "node1"
    node1.vm.network :private_network, ip: "192.168.201.11"
  end

  config.vm.define "node2" do |node2|
    node2.vm.box = "generic/centos8"
    node2.vm.hostname = "node2"
    node2.vm.network :private_network, ip: "192.168.201.12"
  end

  config.vm.define "node3" do |node3|
    node3.vm.box = "generic/centos8"
    node3.vm.hostname = "node3"
    node3.vm.network :private_network, ip: "192.168.201.13"
  end

  #config.vm.provision "shell", inline: <<-SHELL
  #  sudo echo "nameserver  8.8.8.8" > /etc/resolv.conf
  #SHELL

end
