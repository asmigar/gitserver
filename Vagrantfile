Vagrant.configure("2") do |config|
  
  config.vm.define "gitserver" do |git|
  	git.vm.hostname = "gitserver"
  	git.vm.box = "bento/ubuntu-22.04"
  	git.vm.box_version = "202502.21.0"
  	git.vm.network "private_network", type: "dhcp"	
 	git.vm.provision :ansible do |ansible|
    		ansible.playbook = "playbook.yml"
  	end
  end


  config.vm.define "john" do |john|
  	john.vm.hostname = "john"
  	john.vm.box = "bento/ubuntu-22.04"
  	john.vm.box_version = "202502.21.0"
  	john.vm.network "private_network", type: "dhcp"
  end

    config.vm.define "jenny" do |jenny|
    	jenny.vm.hostname = "jenny"
    	jenny.vm.box = "bento/ubuntu-22.04"
    	jenny.vm.box_version = "202502.21.0"
    	jenny.vm.network "private_network", type: "dhcp"
    end


end
