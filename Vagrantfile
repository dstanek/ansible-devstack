# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "dummy"

  config.ssh.forward_agent = true
  config.ssh.private_key_path = "/Users/dstanek/.ssh/rax_id_rsa"

  #config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider :rackspace do |rs|
    rs.server_name = ENV["RAX_SERVER_NAME"]
    rs.username = ENV["OS_USERNAME"]
    rs.api_key = ENV["OS_TOKEN"]
    rs.key_name = ENV["RAX_KEY_NAME"]
    rs.flavor = /8 GB Performance/
    rs.image = /Ubuntu 14.04.*(PVHVM)/
    rs.rackspace_region = ENV.fetch('RAX_REGION', 'iad')
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
