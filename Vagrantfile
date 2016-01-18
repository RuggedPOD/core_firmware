# -*- mode: ruby -*-
# vi: set ft=ruby :

$setup = <<SCRIPT
set -ex

cd /root
apt-get update
apt-get install -y git
git clone https://github.com/ggiamarchi/rpi-debian-builder
cd rpi-debian-builder
echo '
export PATH=$PATH:/root/rpi-debian-builder' >> /root/.bashrc
bash install.sh
SCRIPT

Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.provider 'virtualbox' do |vb|
    vb.customize ['modifyvm', :id, '--memory', '1024']
  end
  config.vm.provision "shell", inline: $setup
end
