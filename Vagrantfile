Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  config.vm.define "manager" do |h|
    h.vm.network "private_network", ip: "10.10.10.10"
    h.vm.hostname = "manager"
  end

  config.vm.define "worker-1" do |h|
    h.vm.network "private_network", ip: "10.10.10.11"
    h.vm.hostname = "worker-1"
  end

  config.vm.define "worker-2" do |h|
    h.vm.network "private_network", ip: "10.10.10.12"
    h.vm.hostname = "worker-2"
  end

  config.vm.provider "virtualbox" do |p|
    p.cpus = 2
    p.memory = 2048
  end
end
