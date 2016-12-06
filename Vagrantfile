#$inline = << EOF
# /bin/echo "192.168.56.100 chef-server" > /etc/hosts
#EOF

# Multi instance
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config| 
  config.ssh.insert_key = false
  config.vm.define "node1" do |node1|
   node1.vm.box = "centos/7" 
    node1.vm.host_name = 'chef-client' 
    node1.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.cpus = 1
      vb.name = 'client1'
    end
    node1.vm.network "private_network", ip: "192.168.56.11" 
    node1.vm.provision "shell" do |s|
      s.path = 'script.sh'
      #s.args = "192.168.56.100"
      #s.args = "chef-server"
    end
  end
  
  config.vm.define "node2" do |node2|
    node2.vm.box = "ubuntu/trusty64" 
    node2.vm.host_name = 'chef-server' 
    node2.vm.provider "virtualbox" do |vb|
      vb.memory = 2048 
      vb.cpus = 1
      vb.name = 'chef-server'
    end
  node2.vm.network "private_network", ip: "192.168.56.100"
 end
  config.vm.define "node3" do |node3|
   node3.vm.box = "ubuntu/trusty64" 
    node3.vm.host_name = 'client-ubuntu' 
    node3.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.cpus = 1
      vb.name = 'client-ubuntu'
    end
    node3.vm.network "private_network", ip: "192.168.56.10" 
   # node3.vm.prvision do |s|
    #  s.inline = "'/bin/echo "192.168.56.100 chef-server" > /etc/hosts'"
    #end
  end
end
