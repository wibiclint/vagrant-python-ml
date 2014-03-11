# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.omnibus.chef_version = :latest

  config.vm.provision "shell", inline: "sudo apt-get -y install build-essential python-dev python-numpy python-setuptools python-scipy libatlas-dev"
  config.vm.provision "shell", inline: "pip install -U scikit-learn"
  
  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["chef/cookbooks"]
    chef.roles_path = "chef/roles"
    chef.data_bags_path = "chef/data_bags"
    chef.add_recipe "apt"
    chef.add_recipe "python"
  end
end
