# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

host_vars = YAML.load_file('ansible/host_vars/default')
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ffuenf/ubuntu-14.04-server-amd64'

  config.vm.network 'private_network', ip: host_vars['vagrant_ip']

  config.ssh.forward_agent = true

  config.ssh.shell = 'bash --noprofile -l'

  config.vm.synced_folder 'src', '/home/vagrant/src', create: true

  config.vm.provider 'virtualbox' do |v|
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'ansible/playbook.yml'
  end
end
