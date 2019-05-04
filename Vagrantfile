Vagrant.configure("2") do |config|

  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    s.inline = <<-SHELL
      echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end
  
	
  #ansible 	
  config.vm.define "mastervm" do |mastervm|
  
  mastervm.vm.box = "centos/7"
  mastervm.vm.hostname = "mastervm"
  mastervm.ssh.forward_agent = true
  mastervm.vm.network "private_network", ip: "192.168.33.6"
  mastervm.vm.provider "virtualbox" do |vb|
  
  vb.cpus = "2"	
  vb.memory = "1024"
  end
  end
  
  
  #loadbalancers
  config.vm.define "lb01" do |lb01|

  lb01.vm.box = "centos/7"
  lb01.vm.hostname = "lb01"
  lb01.ssh.forward_agent = true
  lb01.vm.network "private_network", ip: "192.168.33.7"
  lb01.vm.provider "virtualbox" do |vb|
 
  vb.cpus = "2"	
  vb.memory = "512"
  end
  end
  
  
    
  config.vm.define "lb02" do |lb02|

  lb02.vm.box = "centos/7"
  lb02.vm.hostname = "lb02"
  lb02.ssh.forward_agent = true
  lb02.vm.network "private_network", ip: "192.168.33.8"
  lb02.vm.provider "virtualbox" do |vb|
 
  vb.cpus = "2"	
  vb.memory = "512"
  end
  end
  
 
 
  #appservers
  config.vm.define "apps01" do |apps01|

  apps01.vm.box = "centos/7"
  apps01.vm.hostname = "apps01"
  apps01.ssh.forward_agent = true
  apps01.vm.network "private_network", ip: "192.168.33.9"
  apps01.vm.provider "virtualbox" do |vb|
 
  vb.cpus = "2"	
  vb.memory = "512"
  end
  end
 
  config.vm.define "apps02" do |apps02|
  
  apps02.vm.box = "centos/7"
  apps02.vm.hostname = "apps02"
  apps02.ssh.forward_agent = true
  apps02.vm.network "private_network", ip: "192.168.33.10"
  apps02.vm.provider "virtualbox" do |vb|
 
  vb.cpus = "2"	
  vb.memory = "512"
  end
  end
 
 
  #database
  config.vm.define "db" do |db|
  
  db.vm.box = "centos/7"
  db.vm.hostname = "db"
  db.ssh.forward_agent = true
  db.vm.network "private_network", ip: "192.168.33.11"
  db.vm.provider "virtualbox" do |vb|
 
  vb.cpus = "2"	
  vb.memory = "512"
  end
  end
  

 end