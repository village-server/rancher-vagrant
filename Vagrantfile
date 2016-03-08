# Rancher Workshop Demo
#

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "echo Rancher!"

  config.vm.define "server" do |server|
    server.vm.box = "ubuntu/trusty64"
    server.vm.hostname = "rancher-server.box"
    server.vm.network :private_network, ip: "172.30.0.100"
    server.vm.provision "docker" do |d|
    end
  end

  config.vm.define "host" do |host|
    host.vm.box = "ubuntu/trusty64"
    host.vm.hostname = "rancher-host.box"
    host.vm.network :private_network, ip: "172.30.0.200"
    host.vm.provision "docker" do |d|
    end
  end
end
