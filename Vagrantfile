# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'dduportal/boot2docker'

  config.ssh.forward_agent = true
  config.ssh.private_key_path = [
    '~/.vagrant.d/insecure_private_key',
    '~/.ssh/id_rsa'
  ]

  config.vm.synced_folder '~/src', '/home/docker/src', create: true

  config.vm.provider 'virtualbox' do |vb|
    vb.memory = host_megs_ram / 2
    # use host's resolver mechanism for DNS requests
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
    # proxy DNS requests to host's servers
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
  end

  config.vm.provision 'file', source: 'devbox', destination: '/home/docker/devbox'
end

def host_megs_ram
  case host
  when /darwin/
    `sysctl -n hw.memsize`.to_i / 1025 / 1024
  when /linux/
    `grep 'MemTotal' /proc/meminfo | sed -e 's/MemTotal://' -e 's/ kB//'`.to_i / 1024
  else
    # sorry, no idea
    2048
    kwargs.fetch(:windows).call
  end
end

def host
  RbConfig::CONFIG['host_os']
end
