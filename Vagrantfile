Vagrant.configure("2") do |config|
  config.vm.box = "bento/fedora-31"

  config.vm.provider "virtualbox" do |vb|
      vb.cpus = 2
      vb.memory = 2048
      vb.gui = true
      vb.name = "desktop"

      vb.customize ["modifyvm", :id, "--graphicscontroller", "vboxvga"]
      vb.customize ["modifyvm", :id, "--vram", "64"]
      vb.customize ["modifyvm", :id, "--accelerate2dvideo", "on"]
      vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "./provisioners/main.yml"
  end

  config.vm.provision "file", source: "./dotfiles", destination: "/home/jspengeman/"
end
