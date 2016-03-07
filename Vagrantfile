# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|

  config.vm.define "railsbox"

  config.vm.box = "ubuntu/trusty64"
  config.vm.synced_folder "./", "/var/railsbox"
  config.vm.network "forwarded_port", guest: 3000, host: 3000

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "bootstrap.yml"
    ansible.groups = {
      "database" => ["railsbox"],
      "webserver" => ["railsbox"]
    }
  end
end
