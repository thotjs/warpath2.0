require 'yaml'

vconfig = YAML::load_file("vagrant/config.yml")

VAGRANT_FILE_API_VERSION = "2"

Vagrant.require_version ">= 1.6.3"

Vagrant.configure(VAGRANT_FILE_API_VERSION) do |config|
  (1..vconfig["admin"]["servers"]).each do |i|
    hostname = vconfig["admin"]["hostname"] + "-#{i}"

    config.vm.define hostname do |node|
      node.vm.box = vconfig["admin"]["box"]

      node.vm.box_check_update = true

      node.vm.boot_timeout = vconfig["admin"]["boot_timeout"]
      node.vm.graceful_halt_timeout = vconfig["admin"]["halt_timeout"]
    end
  end
end