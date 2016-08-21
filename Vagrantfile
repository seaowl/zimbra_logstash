# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-7.2"
  config.vm.synced_folder "conf.d/", "/etc/logstash/conf.d/"
  config.vm.synced_folder "patterns/", "/etc/logstash/patterns/"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = 'vagrant/provision/playbook.yml'
    ansible.sudo = true
  end

  config.vm.network 'forwarded_port', guest: 9200, host: 9200
  config.vm.network 'forwarded_port', guest: 9300, host: 9300
  config.vm.network 'forwarded_port', guest: 5000, host: 5000
  config.vm.network 'forwarded_port', guest: 80, host: 9080
  config.vm.network 'forwarded_port', guest: 5601, host: 5601

  config.vm.provider 'parallels' do |v|
    v.update_guest_tools = true
    v.name = 'zbox-caterapp'
    v.memory = 2048
    v.cpus = 2
  end
end
