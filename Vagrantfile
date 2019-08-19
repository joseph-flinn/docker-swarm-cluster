# _*_ mode: ruby _*_
# vi: set ft=ruby
#
# Derived from https://github.com/jamesdmorgan/vagrant-ansible-docker-swarm/blob/master/Vagrantfile

required_plugins = %w( vagrant-host-shell )
required_plugins.each do |plugin|
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

VAGRANTFILE_API_VERSION = "2"
MANAGERS = 1
WORKERS = 2
ANSIBLE_GROUPS = {
  "managers" => ["manager[1:#{MANAGERS}"],
  "workers" => ["worder[1:#{WORKERS}"],
  "all_groups:children" => [
    "managers",
    "workers"
  ]
}


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "peru/ubuntu-18.04-server-amd64"

  (1..MANAGERS).each do |manager_id|
    config.vm.define "manager#{manager_id}" do |manager|
      manager.vm.hostname = "manger#{manager_id}"
      manager.vm.network "private_network", ip: "192.168.50.#{100+manager_id}"
      manager.vm.provider "virtualbox" do |v|
	v.gui = false
        v.memory = 2048
        v.cpus = 2
      end
    end
  end

  (1..WORKERS).each do |worker_id|
    config.vm.define "worker#{worker_id}" do |worker|
      worker.vm.hostname = "worker#{worker_id}"
      worker.vm.network "private_network", ip: "192.168.50.#{110+worker_id}"
      worker.vm.provider "virtualbox" do |v|
	v.gui = false
        v.memory = 2048
        v.cpus = 2
      end
    end
  end
end
