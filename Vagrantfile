hosts = [
    { name: 'vxlan-1', ip: '10.255.255.101' },
    { name: 'vxlan-2', ip: '10.255.255.102' },
]

Vagrant.configure("2") do |config|
    hosts.each do |host|
        config.vm.define host[:name], autostart: true do |node|
            node.vm.box = 'ubuntu/focal64'
            node.vm.hostname = host[:name]
            node.vm.network :private_network, ip: host[:ip]

            node.vm.provider :virtualbox do |vb|
                vb.customize [
                    'modifyvm', :id,
                    '--name', host[:name],
                    '--memory', 512,
                    '--cpus', 1,
                    '--ioapic', 'on',
                    '--nictype1', 'virtio',
                    '--nictype2', 'virtio'
                ]
            end

            node.vm.provision :ansible do |ansible|
                ansible.playbook = 'site.yml'
            end
        end
    end
end
