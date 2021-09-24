N=2
 
Vagrant.configure(2) do |config|
  config.ssh.username = 'devops'
  config.ssh.forward_agent = true
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :vsphere do |vsphere|
    vsphere.host = 'vcsa'
    vsphere.compute_resource_name = 'AlexCluster'
    vsphere.resource_pool_name = ''
    vsphere.vm_base_path = 'k8s'
    vsphere.customization_spec_name = 'u2'
    vsphere.template_name = 'templates/c7ansible'
    vsphere.user = 'Administrator@alex.local'
    vsphere.password = 'P@sw0rd1'
    vsphere.insecure = true
  end

    config.vm.define "k8s-master" do |master|
        master.vm.box = "master"
        master.vm.box_url = "dummy.box"
        master.vm.network "private_network", ip: "192.168.0.62"
        master.vm.hostname = "k8s-master"   	    
        #master.vm.provision "ansible" do |ansible|
        #    ansible.playbook = "kubernetes-setup/master-playbook.yml"
        #    ansible.raw_arguments = ["-b","-u devops"]
        #    ansible.extra_vars = { 
        #          node_ip: "192.168.0.62",
        #    }
        #end
    end

  
#  (1..N).each do |i|
#        config.vm.define "node-#{i}" do |node|
#            node.vm.box = "node"
#            node.vm.box_url = "dummy.box"
#            node.vm.network "private_network", ip: "192.168.0.#{i + 62}"
#            node.vm.hostname = "node-#{i}"
            #node.vm.provision "ansible" do |ansible|
            #    ansible.playbook = "kubernetes-setup/node-playbook.yml"
            #    ansible.raw_arguments = ["-b","-u devops"]
            #    ansible.extra_vars = {
            #        node_ip: "192.168.0.#{i + 62}",
            #    }
            #end
#        end
#    end
end