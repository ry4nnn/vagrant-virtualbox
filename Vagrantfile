IMAGE_NAME = "ubuntu/bionic64"
N = 1

$script = <<-SCRIPT
ifconfig
SCRIPT

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provision "shell", inline: $script

    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
    end
      
    (1..N).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.box = IMAGE_NAME
            node.vm.network "private_network", ip: "192.168.99.#{i + 10}"
            node.vm.hostname = "node-#{i}"
        end
    end
end