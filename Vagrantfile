Vagrant.require_version ">= 2.2.2"

Vagrant.configure(2) do |config|
  config.vm.define "ansible-nas-test" do
    config.vm.box = "ubuntu/bionic64"
    config.vm.network "private_network", ip: "192.168.58.5"
    config.ssh.insert_key = false

    config.vm.provision "ansible_local" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.galaxy_role_file = "requirements.yml"
      ansible.inventory_path = "tests/inventories/integration_testing/inventory"
      ansible.playbook = "nas.yml"
      ansible.become = true
    end
    config.vm.provider "virtualbox" do |v|
      v.memory = 8048
      v.cpus = 4
    end
  end
end
