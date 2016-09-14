# -*- mode: ruby -*-
# vi: set ft=ruby :

# Create Rancher Compatible Host
#

# Config variables
$vb_gui = false
$vb_memory = 1024
$vb_cpus = 1
$rsync_folder_disabled = true

Vagrant.configure("2") do |config|

  # Define VM specs
  config.vm.provider 'virtualbox' do |vb|
    vb.gui = $vb_gui
    vb.memory = $vb_memory
    vb.cpus = $vb_cpus
  end

# Create our Rancher Host
  config.vm.define "rancher-host" do |server|
    server.vm.box = "ubuntu/trusty64"
    server.vm.hostname = "rancher-host"
    server.vm.network "public_network"
    # Have vagrant install docker for convenience
    server.vm.provision "docker" do |d|
    end
  end

  # Disabling compression because OS X has an ancient version of rsync installed.
  # Add -z or remove rsync__args below if you have a newer version of rsync on your machine.
  config.vm.synced_folder '.', '/opt/rancher', type: 'rsync',
      rsync__exclude: '.git/', rsync__args: ['--verbose', '--archive', '--delete', '--copy-links'],
      disabled: $rsync_folder_disabled
end
