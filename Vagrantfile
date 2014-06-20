# -*- mode: ruby -*-
# # vi: set ft=ruby :
#`
# my first vagrantfile with multiple boxes
# Url for boxes : http://puppet-vagrant-boxes.puppetlabs.com/
Vagrant::configure("2") do |config|

  config.hostmanager.enabled = false
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  config.vm.provision :hostmanager

  config.vm.define :puppetmaster do |puppetmaster_config|
    puppetmaster_config.vm.box = "puppetmaster"
    puppetmaster_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-65-x64-virtualbox-nocm.box"
    puppetmaster_config.vm.network :private_network, ip: "192.168.127.100"
    puppetmaster_config.vm.network :private_network, ip: "192.168.100.100"
    #puppetmaster_config.vm.network :public_network, bridge: "em1"
    puppetmaster_config.vm.hostname = "puppet.example.com"
    puppetmaster_config.hostmanager.aliases = %w(puppet puppetmaster.example.com puppetmaster)
    puppetmaster_config.vm.synced_folder "puppet", "/data/puppet", id: "puppet-mod-root", disabled: false
    puppetmaster_config.vm.provider :virtualbox do |vb|
      vb.customize [ 'modifyvm', :id, '--name', "puppetmaster.example.com-#{Time.now.to_i}", "--memory", "1024" ]
      vb.customize [ 'modifyvm', :id, '--nic3', 'hostonly', '--cableconnected3', 'on',  '--hostonlyadapter3', 'vboxnet1']

    end
  end

  config.vm.define :worker1 do |worker1_config|
    worker1_config.vm.box = "worker1"
    worker1_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-65-x64-virtualbox-nocm.box"
    #worker1_config.vm.network :private_network, ip: "192.168.127.101"
    worker1_config.vm.network :private_network, ip: "192.168.100.101"
    #worker1_config.vm.network :public_network, bridge: "em1"
    worker1_config.vm.hostname = "worker1.example.com"
    worker1_config.hostmanager.aliases = %w(worker1)
    worker1_config.vm.synced_folder "puppet", "/data/puppet", id: "puppet-mod-root", disabled: false
    worker1_config.vm.provider :virtualbox do |vb|
      vb.customize [ 'modifyvm', :id, '--name', "uworker1.example.com-#{Time.now.to_i}", "--memory", "512" ]
      vb.customize [ 'modifyvm', :id, '--nic3', 'hostonly', '--cableconnected3', 'on',  '--hostonlyadapter3', 'vboxnet1']
    end
  end

  config.vm.define :worker2 do |worker2_config|
    worker2_config.vm.box = "worker2"
    worker2_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-65-x64-virtualbox-nocm.box"
    #worker2_config.vm.network :private_network, ip: "192.168.127.102"
    worker2_config.vm.network :private_network, ip: "192.168.100.102"
    #worker1_config.vm.network :public_network, bridge: "em1"
    worker2_config.vm.hostname = "worker2.example.com"
    worker2_config.hostmanager.aliases = %w(worker2)
    worker2_config.vm.synced_folder "puppet", "/data/puppet", id: "puppet-mod-root", disabled: false
    worker2_config.vm.provider :virtualbox do |vb|
      vb.customize [ 'modifyvm', :id, '--name', "worker2.example.com-#{Time.now.to_i}", "--memory", "512" ]
      vb.customize [ 'modifyvm', :id, '--nic3', 'hostonly', '--cableconnected3', 'on',  '--hostonlyadapter3', 'vboxnet1']
    end
  end

  config.vm.define :reports do |reports_config|
    reports_config.vm.box = "reports"
    reports_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-65-x64-virtualbox-nocm.box"
    #reports_config.vm.network :private_network, ip: "192.168.127.103"
    reports_config.vm.network :private_network, ip: "192.168.100.103"
    #reports_config.vm.network :public_network, bridge: "em1"
    reports_config.vm.hostname = "reports.example.com"
    reports_config.hostmanager.aliases = %w(reports)
    reports_config.vm.synced_folder "puppet", "/data/puppet", id: "puppet-mod-root", disabled: false
    reports_config.vm.provider :virtualbox do |vb|
      vb.customize [ 'modifyvm', :id, '--name', "reports.example.com-#{Time.now.to_i}", "--memory", "512" ]
      vb.customize [ 'modifyvm', :id, '--nic3', 'hostonly', '--cableconnected3', 'on',  '--hostonlyadapter3', 'vboxnet1']
    end
  end

  config.vm.define :gateway do |gateway_config|
    gateway_config.vm.box = "gateway"
    gateway_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-65-x64-virtualbox-nocm.box"
    gateway_config.vm.network :private_network, ip: "192.168.127.104"
    gateway_config.vm.network :private_network, ip: "192.168.100.104"
    #gateway_config.vm.network :public_network, bridge: "em1"
    gateway_config.vm.hostname = "gateway.example.com"
    gateway_config.hostmanager.aliases = %w(gateway)
    gateway_config.vm.synced_folder "puppet", "/data/puppet", id: "puppet-mod-root", disabled: false
    gateway_config.vm.provider :virtualbox do |vb|
      vb.customize [ 'modifyvm', :id, '--name', "gateway.example.com-#{Time.now.to_i}", "--memory", "512" ]
      vb.customize [ 'modifyvm', :id, '--nic3', 'hostonly', '--cableconnected3', 'on',  '--hostonlyadapter3', 'vboxnet1']
    end
  end

  config.vm.define :node01 do |node01_config|
    node01_config.vm.box = "node01"
    node01_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-65-x64-virtualbox-nocm.box"
    node01_config.vm.network :private_network, ip: "192.168.127.105"
    #node01_config.vm.network :public_network, bridge: "em1"
    node01_config.vm.hostname = "node01.example.com"
    node01_config.hostmanager.aliases = %w(node01)
    node01_config.vm.synced_folder "puppet", "/data/puppet", id: "puppet-mod-root", disabled: false
    node01_config.vm.provider :virtualbox do |vb|
      vb.customize [ 'modifyvm', :id, '--name', "node01.example.com-#{Time.now.to_i}", "--memory", "512" ]
    end
  end

  config.vm.define :node02 do |node02_config|
    node02_config.vm.box = "node02"
    node02_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-65-x64-virtualbox-nocm.box"
    node02_config.vm.network :private_network, ip: "192.168.127.106"
    #node02_config.vm.network :public_network, bridge: "em1"
    node02_config.vm.hostname = "node02.example.com"
    node02_config.hostmanager.aliases = %w(node02)
    node02_config.vm.synced_folder "puppet", "/data/puppet", id: "puppet-mod-root", disabled: false
    node02_config.vm.provider :virtualbox do |vb|
      vb.customize [ 'modifyvm', :id, '--name', "node02.example.com-#{Time.now.to_i}", "--memory", "512" ]
    end
  end

  config.vm.define :git do |git_config|
    git_config.vm.box = "git"
    git_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-65-x64-virtualbox-nocm.box"
    git_config.vm.network :private_network, ip: "192.168.127.150"
    git_config.vm.network :private_network, ip: "192.168.100.150"
    #git_config.vm.network :public_network, bridge: "em1"
    git_config.vm.hostname = "git.example.com"
    git_config.hostmanager.aliases = %w(git)
    git_config.vm.synced_folder "puppet", "/data/puppet", id: "puppet-mod-root", disabled: false
    git_config.vm.provider :virtualbox do |vb|
      vb.customize [ 'modifyvm', :id, '--name', "git.example.com-#{Time.now.to_i}", "--memory", "512" ]
      vb.customize [ 'modifyvm', :id, '--nic3', 'hostonly', '--cableconnected3', 'on',  '--hostonlyadapter3', 'vboxnet1']
    end
  end
end
