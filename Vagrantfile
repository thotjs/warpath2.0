require 'yaml'

vconfig = YAML::load_file("vagrant/config.yml")

VAGRANT_FILE_API_VERSION = "2"

Vagrant.require_version ">= 1.6.3"

web = vconfig["servers"]["web"]
mongo = vconfig["servers"]["mongo"]
redis = vconfig["servers"]["redis"]
admin = vconfig["apps"]["admin"]
api = vconfig["apps"]["api"]
client = vconfig["apps"]["proxy"]
fulfillment = vconfig["apps"]["fulfillment"]
queue = vconfig["apps"]["queue"]
workers = vconfig["apps"]["workers"]

Vagrant.configure(VAGRANT_FILE_API_VERSION) do |config|
  (1..mongo["instances"]).each do |i|
    hostname = mongo["hostname"] + "-#{i}"

    config.vm.define hostname do |node|
      node.vm.box = mongo["box"]

      node.vm.box_check_update = true

      node.vm.boot_timeout = mongo["boot_timeout"]
      node.vm.graceful_halt_timeout = mongo["halt_timeout"]

      node.vm.hostname = hostname

      node.vm.post_up_message = hostname + " is now running}"
    end
  end

  (1..redis["instances"]).each do |i|
    hostname = redis["hostname"] + "-#{i}"

    config.vm.define hostname do |node|
      node.vm.box = redis["box"]

      node.vm.box_check_update = true

      node.vm.boot_timeout = redis["boot_timeout"]
      node.vm.graceful_halt_timeout = redis["halt_timeout"]

      node.vm.hostname = hostname

      node.vm.post_up_message = hostname + " is now running}"
    end
  end

  (1..web["instances"]).each do |i|
    hostname = web["hostname"] + "-#{i}"

    config.vm.define hostname do |node|
      node.vm.box = web["box"]

      node.vm.box_check_update = true

      node.vm.boot_timeout = web["boot_timeout"]
      node.vm.graceful_halt_timeout = web["halt_timeout"]

      node.vm.hostname = hostname

      node.vm.post_up_message = hostname + " is now running}"
    end
  end
end