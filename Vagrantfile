# Vagrant 1.7.2

VAGRANTFILE_API_VERSION = "2"

ENV['ANSIBLE_CONFIG'] = "../../provision/ansible.cfg"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "dev"
    config.vm.network "forwarded_port", guest: 80, host: 8000
    config.vm.network "public_network", bridge: 'en0: Wi-Fi (AirPort)'

    config.ssh.forward_agent = true

    config.vm.synced_folder "../../source", "/var/vagrant/"
    
    config.vm.provision "ansible" do |ansible|

        ansible.limit = "vagrant"
        ansible.inventory_path = "../../environments/vagrant"
        ansible.playbook = "../../provision/vagrant.yml"
        #ansible.verbose = "vvvv"
    end
end
