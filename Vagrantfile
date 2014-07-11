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
            d.volumes = ["/app:/static", "/app/symfony:/app"]
            d.vagrant_vagrantfile = "docker-host/Vagrantfile"
            d.link("symfony-php:php-fpm.docker")
        end
    end

    config.vm.define "php" do |php|
        php.vm.provider :docker do |d|
            d.build_dir = "php-fpm"
            d.cmd = ["php5-fpm", "--allow-to-run-as-root"]
            d.name = "symfony-php"
            d.ports = ["9000:9000"]
            d.volumes = ["/app:/static", "/app/symfony:/app"]
            d.vagrant_vagrantfile = "docker-host/Vagrantfile"
            d.link("symfony-mysql:mysql.docker")
        end
    end

    config.vm.define "mysql" do |mysql|
        mysql.vm.provider :docker do |d|
            d.build_dir = "mysql"
            d.name = "symfony-mysql"
            d.cmd = ["mysqld_safe"]
            d.env = {
            	"MYSQL_PASS" => "symfony-nyccamp"
            	}
            d.ports = ["3306:3306"]
            d.volumes = ["/app/.mysql_data:/var/lib/mysql"]
            d.vagrant_vagrantfile = "docker-host/Vagrantfile"
        end
    end

    config.vm.define "nginx-php" do |nginxphp|
        nginxphp.vm.provider :docker do |d|
            d.build_dir = "nginx-php"
            d.name = "symfony-nginxphp"
            d.cmd = ["/usr/bin/supervisord"]
            d.ports = ["80:80"]
            d.volumes = ["/app/symfony:/app"]
            d.vagrant_vagrantfile = "docker-host/Vagrantfile"
            d.link("symfony-mysql:mysql.docker")
        end
    end
end
