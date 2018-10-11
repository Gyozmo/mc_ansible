require_relative "./config"

Vagrant.configure("2") do |config|
	config.vm.box = "ubuntu/bionic64"
	config.vm.network "public_network", ip: @IP_VM
	config.vm.provision "shell" do |s|
		ssh_pub_key = File.readlines(@SSH_KEY_PATH).first.strip
		s.inline = <<-SHELL
			echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
			echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
			sudo apt-get install -y python
		SHELL
	end
	config.ssh.insert_key = false
	config.vm.provider "virtualbox" do |v|
		v.memory = 1024
		v.cpus = 1
	end
end