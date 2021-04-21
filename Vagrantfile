#Thiago marinho da Silva [thithi]

  $script_mysql = <<-SCRIPT
     apt-get update && \
     apt-get install -y mysql-server-5.7 && \
     cat /vagrant/mysql/mysqld.cnf > /etc/mysql/mysqld.conf.d/mysqld.cnf && \
     service mysql restart
  SCRIPT

  Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.provider "virtualbox" do |vb|
   vb.memory = "1024"
   vb.cpus = 1
  end

  config.vm.define "mysqls" do |mysqls|
  mysqls.vm.network "forwarded_port", guest: 3306, host: 3306

  mysqls.vm.provider "virtualbox" do |vb|
  vb.name = "mysqls"
  end

  mysqls.vm.provision "shell", inline: $script_mysql
  end
end