Vagrant.configure("2") do |config|
  # Configure the first VM
  config.vm.define "centos1" do |node1|
    node1.vm.box = "centos/7"
    node1.vm.network "private_network", ip: "192.168.56.201"
    node1.vm.hostname = "centos1"
    node1.vm.provider "virtualbox" do |vb1|
      vb1.memory = "1024"
    end
    node1.vm.provision "shell", inline: <<-SHELL
      sudo yum install -y git
      sudo yum -y install sshpass net-tools
      sudo sed -i 's/PasswordAuthentication no/#PasswordAuthentication no/' /etc/ssh/sshd_config
      sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
      sudo systemctl restart sshd
      sudo useradd admin
      echo "admin:password" | sudo chpasswd
      echo "admin ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/ansible


    SHELL
  end

  # Configure the second VM
  config.vm.define "centos2" do |node2|
    node2.vm.box = "centos/7"
    node2.vm.network "private_network", ip: "192.168.56.202"
    node2.vm.hostname = "centos2"
    node2.vm.provider "virtualbox" do |vb2|
      vb2.memory = "1024"
    end
    node2.vm.provision "shell", inline: <<-SHELL
      sudo yum install -y git
      sudo yum -y install sshpass net-tools
      sudo sed -i 's/PasswordAuthentication no/#PasswordAuthentication no/' /etc/ssh/sshd_config
      sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
      sudo systemctl restart sshd
      sudo useradd admin
      echo "admin:password" | sudo chpasswd
      echo "admin ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/ansible
    SHELL
  end
end
