# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

host_vars = YAML.load_file('ansible/host_vars/default')
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'jfredett/arch-puppet'

  config.ssh.forward_agent = true

  config.vm.synced_folder 'src', '/home/vagrant/src', create: true

  config.vm.provider 'virtualbox' do |vb|
    vb.memory = 1024
    vb.cpus = 2
    # use host's resolver mechanism for DNS requests
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
    # proxy DNS requests to host's servers
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
  end

  config.vm.provision 'ansible', run: 'always' do |ansible|
    ansible.playbook = 'ansible/playbook.yml'
  end
end
