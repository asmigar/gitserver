Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.box_version = "202502.21.0"

   config.vm.provider "virtualbox" do |vb|
     vb.memory = 1024
     vb.cpus = 1
   end

  config.vm.define "gitserver" do |git|
  	git.vm.hostname = "gitserver"

  	git.vm.network "private_network", type: "dhcp"
 	git.vm.provision :ansible do |ansible|
    		ansible.playbook = "playbook.yml"
  	end
  end

  config.vm.define "john" do |john|
  	john.vm.hostname = "john"
  	john.vm.network "private_network", type: "dhcp"
  end

  config.vm.define "jenny" do |jenny|
    jenny.vm.hostname = "jenny"
    jenny.vm.network "private_network", type: "dhcp"
  end
end
