# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.hostname = "BOX"
  config.vm.box = "bento/ubuntu-18.04"

  config.vm.network "public_network", ip: "192.168.1.99"
  config.vm.box_check_update = false
  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
   end

  # copy local ssh key, install git, tmux
  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "ansible_guest_provisioning.yaml"
    ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
  end

  # copy our tmux conf
  config.vm.provision "file", source: "~/.tmux.conf", destination: ".tmux.conf"

end
