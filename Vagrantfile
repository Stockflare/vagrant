# berkshelf 2.0.14

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Prefer VMware Fusion before VirtualBox
  config.vm.provider "vmware_fusion"
  config.vm.provider "virtualbox"



  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine.
  # [9000].each do |p|
  [2345, 9200, 9300].each do |p|
    config.vm.network :forwarded_port, guest: p, host: p
  end


  # Share an additional folder to the guest VM
  config.vm.synced_folder ".", "/vagrant", :type => "nfs"
  config.vm.synced_folder "../", "/stockflare", :type => "nfs"


  config.vm.provider :virtualbox do |vb, override|
    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "4"]
    vb.name = "api-reuters"
    override.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
    # Every Vagrant virtual environment requires a box to build off of.
    override.vm.box = "trusty"
    override.vm.network :private_network, ip: "192.168.56.89"
  end

  config.vm.provider "vmware_fusion" do |vb, override|
    vb.vmx["memsize"] = "4096"
    vb.vmx["numvcpus"] = "4"
    override.vm.box_url = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vmwarefusion.box"
    override.vm.box = "trusty_fusion"
    override.vm.network :private_network, ip: "192.168.66.89"
  end


  # Bootstrap to Docker
  config.vm.provision :shell, path: "script/vagrant_bootstrap", :privileged => true

end
