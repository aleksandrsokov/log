# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
 config.vm.box = "ubuntu/jammy64"

 config.vm.provider "virtualbox" do |v|
   v.memory = 1024
   v.cpus = 1
 end

 config.vm.define "web" do |web|
   web.vm.network "public_network", ip: "192.168.0.181"
   web.vm.hostname = "web"

   web.vm.provision "shell", inline: <<-SHELL
    mkdir -p ~root/.ssh
    cp ~vagrant/.ssh/auth* ~root/.ssh
    sudo sed -i 's/\PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
    sudo sed -i 's/KbdInteractiveAuthentication no/\#KbdInteractiveAuthentication no/g' /etc/ssh/sshd_config
    systemctl restart sshd
   SHELL

   
 end


 config.vm.define "log" do |log|
   log.vm.network "public_network", ip: "192.168.0.182"
   log.vm.hostname = "log"

  log.vm.provision "shell", inline: <<-SHELL
    mkdir -p ~root/.ssh
    cp ~vagrant/.ssh/auth* ~root/.ssh
    sudo sed -i 's/\PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
    sudo sed -i 's/KbdInteractiveAuthentication no/\#KbdInteractiveAuthentication no/g' /etc/ssh/sshd_config
    systemctl restart sshd
   SHELL


 end


end