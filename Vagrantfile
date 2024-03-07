Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "EzzOps"
  config.vm.box_check_update = false
  # sudo sed -i 's/127.0.0.1/173.212.248.134/' /etc/rancher/k3s/k3s.yaml
  config.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 6443, host: 6443
  # config.vm.synced_folder ".", "/vagrant", nfs: true
  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = "EzzOps"
    vb.memory = "2024"
    vb.cpus = 2
  end
  # config.vm.provision "shell", path: "script.sh"

  # config.vm.provision "ansible" do |ansible|
  #   ansible.verbose = "v"
  #   ansible.playbook = "playbook.yml"
  # end  

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