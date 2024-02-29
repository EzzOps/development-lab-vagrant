Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "EzzOps"

  config.vm.box_check_update = false


  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.network "public_network", 
   use_dhcp_assigned_default_route: true

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder ".", "/vagrant", nfs: true

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = "EzzOps"  
    vb.memory = "1024"
    vb.cpus = 2
  end
  

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
    config.vm.provision "shell", inline: <<-SHELL
      curl -sfL https://get.k3s.io | sh -
    SHELL
  
end


############################################################################################################
#   # Provider for Docker
#   config.vm.provider :docker do |docker, override|
#     override.vm.box = nil
#     docker.image = "rofrano/vagrant-provider:ubuntu"
#     docker.remains_running = true
#     docker.has_ssh = true
#     docker.privileged = true
#     docker.volumes = ["/sys/fs/cgroup:/sys/fs/cgroup:ro"]
#   end
#   # Provision Docker Engine and pull down PostgreSQL
#   config.vm.provision :docker do |d|
#     d.pull_images "postgres:alpine"
#     d.run "postgres:alpine",
#        args: "-d -p 5432:5432 -e POSTGRES_PASSWORD=postgres"
#   end
# end

# vagrant up --provider=docker