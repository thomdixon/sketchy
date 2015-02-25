# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
apt-get update -y &&\
apt-get -y -q install cowsay python-software-properties software-properties-common wget &&\
apt-get install -y python-pip python-dev python-psycopg2 libpq-dev nginx supervisor git curl &&\
apt-get -y install libmysqlclient-dev libxslt-dev libxml2-dev libfontconfig1 &&\
wget -O /usr/local/share/phantomjs-1.9.7-linux-x86_64.tar.bz2 https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-1.9.7-linux-x86_64.tar.bz2 &&\
    tar -xf /usr/local/share/phantomjs-1.9.7-linux-x86_64.tar.bz2 -C /usr/local/share/ &&\
    ln -s /usr/local/share/phantomjs-1.9.7-linux-x86_64/bin/phantomjs /usr/local/bin/phantomjs

cd /app
pip install -e .
SCRIPT

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Puppet Labs' version of Ubuntu works on multiple providers
  config.vm.box = "puppetlabs/ubuntu-14.04-64-puppet"
  config.vm.synced_folder ".", "/app"
  config.vm.provision :shell, :inline => $script
  config.vm.provision :shell, :inline => "/usr/games/cowsay Time to code!"
end
