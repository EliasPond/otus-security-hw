# -*- mode: ruby -*-
# vim: set ft=ruby :
home = ENV['HOME']

MACHINES = {
  :kali => {
    :box_name => "kalilinux/rolling",
    :ip_addr => '192.168.11.101',
    :disks => {
      :sata1 => {
        :dfile => home + '/VirtualBox VMs/kali.vdi',
        :size => 20480,
        :port => 2
      },
    }
  },
  :centos => {
    :box_name => "centos/7",
    :ip_addr => '192.168.11.102',
    :disks => {
      :sata1 => {
        :dfile => home + '/VirtualBox VMs/centos.vdi',
        :size => 10240,
        :port => 2
      },
    }
  }
}

Vagrant.configure("2") do |config|

  MACHINES.each do |boxname, boxconfig|

      config.vm.define boxname do |box|

          box.vm.box = boxconfig[:box_name]
          box.vm.host_name = boxname.to_s

          box.vm.network "private_network", ip: boxconfig[:ip_addr]

          box.vm.provider :virtualbox do |vb|
                  vb.customize ["modifyvm", :id, "--memory", 2048]
                  vb.customize ["modifyvm", :id, "--cpus", 2]
          vb.customize ["storagectl", :id, "--name", "SATA", "--add", "sata" ]

          boxconfig[:disks].each do |dname, dconf|
              unless File.exist?(dconf[:dfile])
                vb.customize ['createhd', '--filename', dconf[:dfile], '--variant', 'Fixed', '--size', dconf[:size]]
              end
              vb.customize ['storageattach', :id,  '--storagectl', 'SATA', '--port', dconf[:port], '--device', 0, '--type', 'hdd', '--medium', dconf[:dfile]]
          end
       end
    end
  end
end
