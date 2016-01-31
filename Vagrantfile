# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192"
    vb.cpus = 4
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    # Swift normal dev / runtime requirements
    sudo apt-get install -y clang libicu-dev
    # Swift compiler dev requirements
    sudo apt-get install -y git cmake ninja-build clang python uuid-dev libicu-dev icu-devtools \
      libbsd-dev libedit-dev libxml2-dev libsqlite3-dev swig libpython-dev libncurses5-dev pkg-config

    # Ubuntu 14.04 requires upgraded clang with C++14 support
    sudo apt-get install -y clang-3.6
    sudo update-alternatives --install /usr/bin/clang clang /usr/bin/clang-3.6 100
    sudo update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-3.6 100
  SHELL
end
