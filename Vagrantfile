# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.hostname = "web"
  config.vm.network "forwarded_port", guest: "8081", host: "8081"
  config.vm.network "forwarded_port", guest: "8082", host: "8082"
  config.vm.network "forwarded_port", guest: "8083", host: "8083"
  config.vm.network "private_network", ip: "192.168.56.10"
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 4
    vb.memory = 4096
  end

  ssh_pub_key = File.readlines("../id_rsa.pub").first.strip
  config.vm.provision "shell", inline: <<-SHELL
    echo #{ssh_pub_key} >> ~vagrant/.ssh/authorized_keys
    echo #{ssh_pub_key} >> ~root/.ssh/authorized_keys
    sudo sed -i 's/\#PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
    #systemctl restart sshd
  SHELL

end
