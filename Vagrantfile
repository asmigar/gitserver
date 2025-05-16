Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.box_version = "202502.21.0"
  developers = ["john", "lara"]

   config.vm.provider "virtualbox" do |vb|
     vb.memory = 1024
     vb.cpus = 1
   end

  config.vm.define "gitserver" do |git|
  	git.vm.hostname = "gitserver"
 	git.vm.provision :ansible do |ansible|
        ansible.playbook = "provisioning/git_playbook.yml"
  	end
  	git.vm.network "private_network", ip: "192.168.50.4"
  end

  developers.each do |developer|
    config.vm.define "#{developer}" do |dev|
  	    dev.vm.hostname = "#{developer}"
  	    dev.vm.provision :ansible do |ansible|
            ansible.playbook = "provisioning/playbook.yml"
        end
        dev.vm.network "private_network", type: "dhcp"
        dev.vm.post_up_message ="Login into #{developer} VM to start using gitserver. For more details: https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server"
    end
  end
end
