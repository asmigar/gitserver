Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.box_version = "202502.21.0"
  config.vm.network "private_network", type: "dhcp"

   config.vm.provider "virtualbox" do |vb|
     vb.memory = 1024
     vb.cpus = 1
   end

  config.vm.define "gitserver" do |git|
  	git.vm.hostname = "gitserver"
 	git.vm.provision :ansible do |ansible|
        ansible.playbook = "git_playbook.yml"
  	end
  end

  config.vm.define "john" do |john|
  	john.vm.hostname = "john"
  	john.vm.provision :ansible do |ansible|
        ansible.playbook = "playbook.yml"
    end
  end

  config.vm.define "lara" do |lara|
    lara.vm.hostname = "lara"
    lara.vm.provision :ansible do |ansible|
        ansible.playbook = "playbook.yml"
    end
  end
end
