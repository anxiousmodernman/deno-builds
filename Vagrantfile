# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 4
  end

  config.vm.provision "shell", inline: <<-SHELL
    yum update
    yum install -y git glibc-static curl vim gcc clang wget
    wget https://nodejs.org/dist/v10.15.3/node-v10.15.3-linux-x64.tar.xz
    tar --strip-components 1 -xvf node-v* -C /usr/local
  SHELL

  $script = <<-SHELL
    curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain \"nightly\"
    git clone --recurse-submodules https://github.com/denoland/deno.git
    cd deno
    sed -i '/default_args/a use_sysroot = false' .gn
  SHELL

  config.vm.provision "shell", inline: $script, privileged: false

  # To build:
  # vagrant up
  # vagrant ssh
  # cd deno
  # ./tools/setup.py
  # ./tools/build.py
  #
  # Sometimes I have to run the build twice :(
  #
  # After a successful build, get the binary out from the host machine:
  # scp -i .vagrant/machines/default/virtualbox/private_key -P 2222 vagrant@127.0.0.1:/home/vagrant/deno/target/debug/deno .
  
end
