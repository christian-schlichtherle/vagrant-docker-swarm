docker_worker_count = ENV['DOCKER_WORKER_COUNT']&.to_i || 2

Vagrant.configure "2" do |config|

  config.vm.box = "ubuntu/bionic64"

  config.vm.define "manager" do |h|
    h.vm.network "private_network", ip: "10.10.10.10"
    h.vm.hostname = "manager"
    h.vm.provision "docker" do |d|
      d.post_install_provision "shell", inline: <<-SCRIPT
        docker swarm init --advertise-addr 10.10.10.10
        docker swarm join-token --quiet worker > /vagrant/docker-swarm-token
      SCRIPT
    end
  end

  (1..docker_worker_count).each do |i|
    worker_name = "worker-#{i}"
    worker_ip = "10.10.10.#{10 + i}"
    config.vm.define worker_name do |h|
      h.vm.network "private_network", ip: worker_ip
      h.vm.hostname = worker_name
      h.vm.provision "docker" do |d|
        d.post_install_provision "shell",
          inline: "docker swarm join --advertise-addr #{worker_ip} --token $(cat /vagrant/docker-swarm-token) 10.10.10.10"
      end
    end
  end

  config.vm.provider "virtualbox" do |p|
    p.cpus = 2
    p.memory = 2048
  end
end
