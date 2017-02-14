# How many Kube nodes do we want?
NUM_NODES = 3

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.box_check_update = false
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider "libvirt" do |domain|
    domain.cpus = 2
    domain.memory = "2048"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 2
    vb.memory = "2048"
  end

  config.ssh.insert_key = false

  (1..NUM_NODES).each do |node_id|
    config.vm.define "node#{node_id}" do |node|
      node.vm.hostname = "node#{node_id}"
      node.vm.network "private_network", ip: "192.168.77.#{20+node_id}", auto_config: false
  
      # We don't want to deal with the host-only interface
      node.vm.provision "shell",
        inline: "ip route del default dev eth0"

      # Only execute once the Ansible provisioner,
      # when all the nodes are up and ready.
      if node_id == NUM_NODES
        node.vm.provision :ansible do |ansible|
          # Disable default limit to connect to all the nodes
          ansible.limit = "all"
	  ansible.verbose = "-vv"
          ansible.playbook = "playbook.yml"
        end
      end
    end
  end
end
