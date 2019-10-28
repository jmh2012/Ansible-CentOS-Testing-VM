VAGRANTFILE_API_VERSION = "2"

TEST_MODE = false

PROVIDER_UNDER_TEST = "virtualbox"
NETWORK_PRIVATE_IP_PREFIX = "172.16.3."

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false

  # VirtualBox.
  config.vm.provider :virtualbox do |v|
    v.gui = false
    v.memory = 1024
    v.cpus = 1
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end
  # CentOS 6
  config.vm.define "centos6" do |centos6|
    centos6.vm.hostname = "centos6test"
    if not TEST_MODE
      centos6.vm.box = "geerlingguy/centos6"
    else
      centos6.vm.box = LOCAL_BOX_DIRECTORY + PROVIDER_UNDER_TEST + "-centos6.box"
    end
    centos6.vm.network :private_network, ip: NETWORK_PRIVATE_IP_PREFIX + "5"

    # Ansible.
    centos6.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.extra_vars = {
        upgrade: ENV['VM_UPGRADE_PKG']
      }
    end
  end
  # CentOS 7
  config.vm.define "centos7" do |centos7|
    centos7.vm.hostname = "centos7test"
    if not TEST_MODE
      centos7.vm.box = "geerlingguy/centos7"
    else
      centos7.vm.box = LOCAL_BOX_DIRECTORY + PROVIDER_UNDER_TEST + "-centos7.box"
    end
    centos7.vm.network :private_network, ip: NETWORK_PRIVATE_IP_PREFIX + "5"

    # Ansible.
    centos7.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.extra_vars = {
        upgrade: ENV['VM_UPGRADE_PKG']
      }
    end
  end
  # CentOS 8
  config.vm.define "centos8" do |centos8|
    centos8.vm.hostname = "centos8test"
    if not TEST_MODE
      centos8.vm.box = "geerlingguy/centos8"
    else
      centos8.vm.box = LOCAL_BOX_DIRECTORY + PROVIDER_UNDER_TEST + "-centos8.box"
    end
    centos8.vm.network :private_network, ip: NETWORK_PRIVATE_IP_PREFIX + "5"

    # Ansible.
    centos8.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.extra_vars = {
        upgrade: ENV['VM_UPGRADE_PKG']
      }
    end
  end
end
