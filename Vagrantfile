# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'jfredett/arch-puppet'

  config.ssh.forward_agent = true

  config.vm.synced_folder 'src', '/home/vagrant/src', create: true

  config.vm.provider 'virtualbox' do |vb|
    vb.memory = 3072
    vb.cpus = 3
    # use host's resolver mechanism for DNS requests
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
    # proxy DNS requests to host's servers
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
  end

  config.vm.provision 'file',
    source: 'locale.conf',
    destination: '~/.config/locale.conf'

  config.vm.provision 'shell', inline: 'yes | pacman -Syu'

  config.vm.provision 'puppet' do |p|
    p.manifest_file = 'init.pp'
    p.module_path = 'modules'
  end
end
