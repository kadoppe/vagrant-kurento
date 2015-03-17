# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "trusty-amd64-current"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

  if Vagrant.has_plugin?("vagrant-hostsupdater")
    config.hostsupdater.remove_on_suspend = true
  end

  config.vm.hostname = "kurento.dev"
  config.vm.network :private_network, ip: "172.17.8.23"

  config.vm.provision :shell, :inline => <<-EOS
    add-apt-repository ppa:kurento/kurento
    apt-get update -y
    apt-get install -y kurento-media-server
    service kurento-media-server start
  EOS
end
