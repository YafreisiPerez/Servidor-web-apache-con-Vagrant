Vagrant.configure("2") do |config|
    # Usa la imagen base de Ubuntu
    config.vm.box = "ubuntu/bionic64"
  
    # Asignar IP estática
    config.vm.network "private_network", ip: "192.168.33.10"
  
    # Asignar recursos
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Sincronizar la carpeta local con la VM
    config.vm.synced_folder "./web", "/var/www/html"
  
    # Provisionar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
  