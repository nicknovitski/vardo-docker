# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'jfredett/arch-puppet'

  config.ssh.forward_agent = true
  config.ssh.shell = 'bash --noprofile -l'
  config.ssh.private_key_path = [
    '~/.vagrant.d/insecure_private_key',
    '~/.ssh/id_rsa'
  ]

  config.vm.synced_folder 'src', '/home/vagrant/src', create: true

  config.vm.provider 'virtualbox' do |vb|
    vb.cpus = host_cpus
    vb.memory = host_megs_ram / 2
    # use host's resolver mechanism for DNS requests
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
    # proxy DNS requests to host's servers
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
  end

  config.vm.provision 'file', source: 'locale.conf',
                              destination: '~/.config/locale.conf'

  config.vm.provision 'shell', inline: 'yes | pacman -Syu'

  config.vm.provision 'puppet' do |p|
    p.manifest_file = 'init.pp'
    p.module_path = 'modules'
  end
end

def host_cpus
  case_host(
    :osx     => -> { `sysctl -n hw.ncpu`.to_i },
    :linux   => -> { `nproc`.to_i },
    :windows => -> { 2 }
  )
end

def host_megs_ram
  case_host(
    :osx     => -> { `sysctl -n hw.memsize`.to_i / 1025 / 1024 },
    :linux   => -> { `grep 'MemTotal' /proc/meminfo | sed -e 's/MemTotal://' -e 's/ kB//'`.to_i / 1024 },
    :windows => -> { 2048 }
  )
end

def case_host(kwargs)
  case host
  when /darwin/
    kwargs.fetch(:osx).call
  when /linux/
    kwargs.fetch(:linux).call
  else
    kwargs.fetch(:windows).call
  end
end

def host
  RbConfig::CONFIG['host_os']
end
