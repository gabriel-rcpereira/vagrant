$script = <<-SCRIPT
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \\
sudo chmod +x /usr/local/bin/docker-compose && \\
SCRIPT

$scriptDocker = <<-SCRIPT
cd /vagrant/ & \\
docker-compose up & -d \\
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest: 8080, host: 8083
  config.vm.network "forwarded_port", guest: 8081, host: 8081
  config.vm.network "forwarded_port", guest: 80, host: 8082
  config.vm.network "forwarded_port", guest: 27017, host: 27017
  config.vm.network "forwarded_port", guest: 9092, host: 9092
  config.vm.network "forwarded_port", guest: 29092, host: 29092
  config.vm.network "forwarded_port", guest: 2181, host: 2181
  config.vm.network "public_network"
  config.vm.synced_folder "../../", "/usr/dev"
  config.vm.provision "shell", inline: $script
  
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end  
  
  ####### Provision #######
  config.vm.provision "docker" do |docker|
    docker.post_install_provision "shell", inline: $scriptDocker
  end

  ## config.vm.provision "docker" do |docker|
  ##   docker.post_install_provision "shell", inline: $scriptDocker
  ##   docker.build_image "/vagrant",
  ##     args: "-t example/hello_web"
  ##   docker.run "hello_web",
  ##     image: "example/hello_web:latest",
  ##     args: "-p 80:80"
  ## end
end