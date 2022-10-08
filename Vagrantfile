Vagrant.require_version ">= 2.0.0"

boxes = [
    {
        :name => "web1",
        :eth1 => "192.168.205.121",
        :mem => "2048",
        :cpu => "1"
    },
    {
        :name => "web2",
        :eth1 => "192.168.205.122",
        :mem => "2048",
        :cpu => "1"
    },
    {
        :name => "db",
        :eth1 => "192.168.205.123",
        :mem => "2048",
        :cpu => "1"
    }

]

Vagrant.configure(2) do |config|
  config.vm.box = "generic/ubuntu2004"

  boxes.each do |opts|
      config.vm.define opts[:name] do |config|
        config.vm.hostname = opts[:name]
        config.vm.provider "virtualbox" do |v|
          v.customize ["modifyvm", :id, "--memory", opts[:mem]]
          v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
          v.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
          v.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]
        end
        config.vm.network :private_network, ip: opts[:eth1]
      end
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt update
  SHELL

end
