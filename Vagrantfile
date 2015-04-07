# coding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

$shell = <<SCRIPT
sudo -u postgres createuser -d -S -R eccube_db_user
sudo -u postgres createdb -U eccube_db_user -E utf-8 eccube_db
echo 'Congratulations!!! Install Success. Please access http://localhost:10080'
SCRIPT


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "nrel/CentOS-6.5-x86_64"
  config.vm.hostname = "centos"

  config.vm.network :forwarded_port, guest: 80, host: 10080
  config.vm.network :forwarded_port, guest: 443, host: 10443
  config.vm.network :forwarded_port, guest: 5432, host: 15432
  config.vm.synced_folder "eccube", "/var/www/eccube", create: true, owner: "vagrant", group: "vagrant", mount_options: ["dmode=777", "fmode=666"]

  config.vm.provision :chef_solo do |chef|
    chef.log_level = :info
    chef.cookbooks_path = ["chef/cookbooks", "chef/site-cookbooks"]

    chef.roles_path = "chef/roles"
    chef.data_bags_path = "chef/data_bags"

    chef.add_recipe     "iptables::disabled"
    chef.add_recipe     "apache2"
    chef.add_recipe     "apache2::mod_php5"
    chef.add_recipe     "apache2::mod_ssl"
    chef.add_recipe     "apache2::mod_rewrite"
    chef.add_recipe     "php"
    chef.add_recipe     "postgresql::client"
    chef.add_recipe     "postgresql::server"

    chef.json = {
      :apache => {
        :version => "2.2",
        :default_site_enabled => true,
        :docroot_dir => "/var/www/eccube/html",
        :listen_ports => [80, 443]
      },
      :php => {
        # :version => "5.3",
        :directives => {
          :display_errors => 'On',
          "date.timezone" => "Asia/Tokyo",
        },
        :packages => ["php-mbstring", "php-pgsql", "php-pear", "php-xml", "php-gd", "php-devel"]
      },
      :postgresql => {
        :password => {
          postgres: 'postgres'
        },
        :pg_hba => [
          {:type => 'local', :db => 'all', :user => 'postgres', :addr => nil, :method => 'trust'},
          {:type => 'local', :db => 'all', :user => 'all', :addr => nil, :method => 'trust'},
          {:type => 'host', :db => 'all', :user => 'all', :addr => '127.0.0.1/32', :method => 'trust'},
          {:type => 'host', :db => 'all', :user => 'all', :addr => '::1/128', :method => 'trust'}
        ]
      }
    }
  end

  config.omnibus.chef_version = '11.12.4'
  # config.berkshelf.enabled = true

  config.vm.provision "shell", inline: $shell
end
