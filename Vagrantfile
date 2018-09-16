$script = <<SCRIPT
#!/bin/bash
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install docker-ce -y
sudo docker swarm init
sudo docker stack deploy -c /vagrant/containers/docker-compose.yml igs 

SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provision "shell", inline: $script  
  
  config.vm.network :forwarded_port, guest: 8080, host: 8089
  config.vm.network :forwarded_port, guest: 8081, host: 8081
  config.vm.network :forwarded_port, guest: 8082, host: 8082
end
