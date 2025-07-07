VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Control node
  config.vm.define "control" do |inventory|
    inventory.vm.hostname = "control"
    inventory.vm.box = "rockylinux/9"
    inventory.vm.network :private_network, ip: "192.168.56.71"

    inventory.vm.provider :virtualbox do |v|
      v.memory = 2048
      v.cpus = 2
      v.linked_clone = false
    end
  end

  # K3S Server
  config.vm.define "server" do |inventory|
    inventory.vm.hostname = "k3s-server01"
    inventory.vm.box = "rockylinux/9"
    inventory.vm.network :private_network, ip: "192.168.56.72"

    inventory.vm.provider :virtualbox do |v|
      v.memory = 2048
      v.cpus = 2
      v.linked_clone = false
    end
  end

  # K3S Agent (Worker)
  config.vm.define "worker" do |inventory|
    inventory.vm.hostname = "k3s-worker01"
    inventory.vm.box = "rockylinux/9"
    inventory.vm.network :private_network, ip: "192.168.56.74"

    inventory.vm.provider :virtualbox do |v|
      v.memory = 4096
      v.cpus = 4
      v.linked_clone = false
    end
  end
end
