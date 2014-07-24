VAGRANT_FILE_API_VERSION = "2"

Vagrant.require_version ">= 1.6.3"

Vagrant.configure(VAGRANT_FILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "chef/fedora-20"
  config.vm.provision :shell, path: "server/bootstrap.sh"
  config.vm.network :forwarded_port, host: 8080, guest: 80
end