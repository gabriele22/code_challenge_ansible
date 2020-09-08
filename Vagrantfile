require_relative './vagrant/key_authorization'

Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/xenial64'
  authorize_key_for_root config, '~/.ssh/id_dsa.pub', '~/.ssh/id_rsa.pub'

  {
    'vm1'    => '192.168.33.10',
    'vm2'   => '192.168.33.11',
  }.each do |short_name, ip|
    config.vm.define short_name do |host|
      host.vm.network 'private_network', ip: ip
      host.vm.hostname = "#{short_name}.codechallenge.dev"
    end
  end
end
