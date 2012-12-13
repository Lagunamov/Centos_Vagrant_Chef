# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  # VM settings
  config.vm.box = "centos"
  #config.vm.box = "CentOS-6.3-x86_64-minimal"
  config.vm.box_url = "https://dl.dropbox.com/u/7225008/Vagrant/CentOS-6.3-x86_64-minimal.box"

  # Network settings
  config.vm.host_name = "lampsrv"
  config.vm.network :hostonly, "192.168.56.99"
  config.vm.share_folder "www", "/var/www/html", "www"

  # Enable provisioning with chef solo
  config.vm.provision :chef_solo do |chef|
	chef.cookbooks_path = "cookbooks"
    	chef.add_recipe "yum"
    	chef.add_recipe "yum::epel"
    	chef.add_recipe "openssl"
    	chef.add_recipe "apache2"
    	chef.add_recipe "apache2::default"
    	chef.add_recipe "apache2::mod_ssl"
    	chef.add_recipe "mysql"
    	chef.add_recipe "mysql::server"
    	chef.add_recipe "php"
    	chef.add_recipe "php::module_apc"
    	chef.add_recipe "php::module_curl"
    	chef.add_recipe "php::module_mysql"
    	chef.add_recipe "apache2::mod_php5"
    	chef.add_recipe "apache2::mod_rewrite"
   	  chef.json = {
        	:mysql => {
            		:server_root_password => 'root',
            		:bind_address => '127.0.0.1'
        	}
    	} 
  end
end
