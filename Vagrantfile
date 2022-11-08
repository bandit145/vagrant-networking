Vagrant.configure("2") do |config|

  config.vm.define "network" do |network|
    network.vm.box = "generic/centos9s"
    network.vm.network "private_network", ip: "fd00:0:0:1::2"
  end

  config.vm.define "box1" do |box1|
    box1.vm.box = "generic/centos9s"
    box1.vm.network "private_network", ip: "fd00:0:0:1::3",
      auto_config: false
    # box1.vm.provider "virtualbox" do |vb|
    #   vb.customize ["modifyvm", :id, "--nic2", "hostonly", "vboxnet2"]
    # end
  end

end