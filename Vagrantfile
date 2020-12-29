Vagrant.configure("2") do |config|
  # Ubuntu Focal
  config.vm.box = "ubuntu/focal64"
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--memory", "8192"]
    v.customize ["modifyvm", :id, "--cpus", "6"]
    
    # Fix for slow Ubuntu Focal boot time
    v.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]
  end
  # End of Ubuntu Focal config
  
  config.vm.network :private_network, ip: "10.1.1.2"
  
  config.vm.provision "ansible" do |ansible|
    #ansible.verbose            =   "v"
    ansible.compatibility_mode  =   "2.0"
    
    ansible.become              =   true
    
    ansible.galaxy_roles_path   =   "roles"
    ansible.galaxy_role_file    =   "requirements.yml"
    
    ansible.playbook            =   "playbook.yml"
    ansible.inventory_path      =   "inventories/vagrant/inventory"
    
    ansible.limit               =   "all"
    
    ansible.extra_vars          =   {
      ansible_user:                 "vagrant",
      ansible_ssh_private_key_file: "~/.vagrant.d/insecure_private_key"
    }
  end
  
end
