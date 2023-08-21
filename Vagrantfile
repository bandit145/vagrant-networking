Vagrant.configure("2") do |config|

  config.vm.define "network" do |network|
    network.vm.box = "generic/centos9s"
    network.vm.network "private_network", ip: "fd00:0:0:1::2"
    network.vm.network "private_network", ip: "192.168.30.2"
    network.vm.provision "shell",
      inline: "dnf install -y epel-release && dnf install -y radvd unbound tcpdump && sysctl -w net.ipv4.ip_forward=1 && sysctl -w net.ipv6.conf.all.forwarding=1"
  end

  config.vm.define "box1" do |box1|
    box1.vm.box = "generic/centos9s"
    box1.vm.network "private_network", ip: "fd00:0:0:1::3"
    box1.vm.network "private_network", ip: "192.168.30.3"
    box1.vm.provision "shell",
      inline: "dnf install -y unbound bind-utils tcpdump && sysctl -w net.ipv4.ip_forward=1 && sysctl -w net.ipv6.conf.all.forwarding=1"
    # box1.vm.provider "virtualbox" do |vb|
    #   vb.customize ["modifyvm", :id, "--nic2", "hostonly", "vboxnet2"]
    # end
  end

end