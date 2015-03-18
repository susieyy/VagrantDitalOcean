# -*- mode: ruby -*-
# vi: set ft=ruby :

Dotenv.load

# change default provider to digital_ocean
ENV['VAGRANT_DEFAULT_PROVIDER'] = "digital_ocean"

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.provider :digital_ocean do |provider, override|
    override.vm.hostname          = "dokku"
    override.vm.box               = "digital_ocean"
    override.vm.box_url           = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
    override.ssh.username         = ENV['SSH_USERNAME']
    override.ssh.private_key_path = ENV['SSH_KEY']

    provider.token                = ENV['DIGITAL_OCEAN_TOKEN']
    provider.ssh_key_name         = "vagrant"
    provider.region               = "sgp1"
    provider.image                = "ubuntu-14-04-x64"
    provider.size                 = "2GB" # 512MB | 1GB | 2GB | 4GB | 8GB | 16GB
    provider.private_networking   = true
    provider.setup                = true

    # disable synced_folder: rsync is not installed on DigitalOcean's guest machine
    override.vm.synced_folder "./", "/vagrant", disabled: true
  end

end
