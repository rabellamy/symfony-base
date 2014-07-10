# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.define "app" do |app|
        app.vm.provider :docker do |d|
            d.build_dir = "nginx"
            d.cmd = ["nginx"]
            d.name = "symfony-nginx"
            d.ports = ["80:80"]
            d.volumes = ["/vagrant:/usr/local/nginx/html"]
            d.vagrant_vagrantfile = "docker-host/Vagrantfile"
        end
    end
end
