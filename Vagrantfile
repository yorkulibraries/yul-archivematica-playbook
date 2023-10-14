# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = ENV.fetch("VAGRANT_BOX", "ubuntu/jammy64")

  {
    "am-local" => {
      "memory" => "4096",
      "cpus" => "8",
    },
  }.each do |short_name, properties|

    # Define guest
    config.vm.define short_name do |host|
      host.vm.hostname = "#{short_name}.myapp.dev"
    end

    # Set the amount of RAM and virtual CPUs for the virtual machine
    config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", properties.fetch("memory")]
      vb.customize ["modifyvm", :id, "--cpus", properties.fetch("cpus")]
    end

  end

  config.vm.network :forwarded_port, guest: 8000, host: 8000
  config.vm.network :forwarded_port, guest: 80, host: 8001

  config.vm.provision :ansible do |ansible|
    ansible.compatibility_mode = "auto"
    ansible.playbook = "playbook.yml"
    ansible.galaxy_role_file = "requirements.yml"
    ansible.galaxy_command = "ansible-galaxy install --role-file=%{role_file}"
    ansible.limit = "all"
    ansible.raw_arguments = "--ask-vault-pass"
    ansible.inventory_path = "inventory/dev"
  end
end
