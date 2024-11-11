# Vagrantfile para configurar una VM con Apache
Vagrant.configure("2") do |config|
    # Seleccionar la imagen base de Ubuntu
    config.vm.box = "ubuntu/bionic64"
  
    # Configurar la red
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Configurar la cantidad de recursos asignados
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Provisión para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  
    # Compartir el directorio local con el directorio de Apache en la VM
    config.vm.synced_folder "./html", "/var/www/html"
  end
  