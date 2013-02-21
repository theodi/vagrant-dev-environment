# -*- mode: ruby -*-
Vagrant::Config.run do |config|

  config.vm.define :odi do |odi_config|
    odi_config.vm.host_name = "odi-vagrant"
    odi_config.vm.box = "precise64"
    odi_config.vm.network :hostonly, "33.33.33.100"

    odi_config.vm.provision :chef_client do |chef|
      chef.node_name = "vagrant-%s" % [
        ENV["USER"]
      ]
      chef.chef_server_url = "https://chef.theodi.org"
      chef.provisioning_path = "/etc/chef"
      chef.knife_config = "./.chef/knife.rb"
      chef.validation_client_name = "chef-validator"
      chef.validation_key_path = ".chef/chef-validator.pem"
      chef.run_list = chef.run_list = [
        "recipe[apt]",
        "recipe[nginx]"
      ]
    end
  end

end
