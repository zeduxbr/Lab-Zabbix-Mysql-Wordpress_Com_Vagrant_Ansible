Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    vb.cpus = 1
  end

  config.vm.define "wordpress" do |wordpress|
    wordpress.vm.network "public_network", ip: "192.168.0.33", bridge: "wlan0"
    wordpress.vm.provision "shell", inline: "cat /configs/id_rsa.pub >> .ssh/authorized_keys"
    wordpress.vm.synced_folder "./configs", "/configs"
  end

  config.vm.define "mysqldb" do |mysqldb|
    mysqldb.vm.network "public_network", ip: "192.168.0.34", bridge: "wlan0"
    mysqldb.vm.provision "shell", inline: "cat /configs/id_rsa.pub >> .ssh/authorized_keys"
    mysqldb.vm.synced_folder "./configs", "/configs"
  end  
 
  config.vm.define "zabbix" do |zabbix|
    zabbix.vm.network "public_network", ip: "192.168.0.35", bridge: "wlan0"
    zabbix.vm.provision "shell", inline: "cat /configs/id_rsa.pub >> .ssh/authorized_keys"
    zabbix.vm.synced_folder "./configs", "/configs"
      
    zabbix.vm.provider "virtualbox" do |vb|
      vb.memory = 8192
      vb.cpus = 6
    end
  end
end