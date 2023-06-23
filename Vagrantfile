# Vagrantfile

Vagrant.configure("2") do |config|

  # Control Node Configuration
  config.vm.define "control" do |node|
    node.vm.box = "centos/7"
    node.vm.hostname = "control.example.com"
    node.vm.network "private_network", ip: "192.168.56.210"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
    node.vm.provision "shell", inline: <<-SHELL
      sudo yum update -y
      sudo yum install -y epel-release
      sudo yum install -y ansible
      sudo useradd -m ansible
      echo "redhat123" | sudo passwd --stdin ansible
      echo "ansible ALL=(ALL) NOPASSWD:ALL" | sudo tee -a /etc/sudoers.d/ansible
      sudo sed -i 's/PasswordAuthentication no/#PasswordAuthentication no/' /etc/ssh/sshd_config
      sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
      sudo systemctl restart sshd
    SHELL
  end

  # Client Machine 1 Configuration
  config.vm.define "client1" do |node|
    node.vm.box = "centos/7"
    node.vm.hostname = "client1.example.com"
    node.vm.network "private_network", ip: "192.168.56.211"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
    node.vm.provision "shell", inline: <<-SHELL
      sudo yum update -y
      sudo useradd -m ansible
      echo "redhat123" | sudo passwd --stdin ansible
      echo "ansible ALL=(ALL) NOPASSWD:ALL" | sudo tee -a /etc/sudoers.d/ansible
      sudo sed -i 's/PasswordAuthentication no/#PasswordAuthentication no/' /etc/ssh/sshd_config
      sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
    SHELL
  end

  # Client Machine 2 Configuration
  config.vm.define "client2" do |node|
    node.vm.box = "centos/7"
    node.vm.hostname = "client2.example.com"
    node.vm.network "private_network", ip: "192.168.56.212"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
    node.vm.provision "shell", inline: <<-SHELL
      sudo yum update -y
      sudo useradd -m ansible
      echo "redhat123" | sudo passwd --stdin ansible
      echo "ansible ALL=(ALL) NOPASSWD:ALL" | sudo tee -a /etc/sudoers.d/ansible
      sudo sed -i 's/PasswordAuthentication no/#PasswordAuthentication no/' /etc/ssh/sshd_config
      sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
      sudo systemctl restart sshd
    SHELL
  end
end
