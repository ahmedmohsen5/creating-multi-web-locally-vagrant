Vagrant.configure("2") do |config|
    config.hostmanager.enable = true
    config.hostmanager.manage_host = true

    ["web01" , "app01" , "db01", "mc01", "rmq01" ].each_with_index do |vm_name, index|
        config.vm.define vm_name do |vm|
            vm.vm.box = "ubuntu20.box"
            vm.vm.hostname = vm_name
            vm.vm.network "private_network", ip: "192.168.56.1#{index + 10}"
            vm.vm.provider "virtualbox" do |vb|
                vb.memory = index < 3 ? '800' : '600'
            end
            vm.vm.provision "shell", inline: <<-SHELL
                 echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDrZ8PeAjUb3vJkO5AVpGxZKHPMpDCCZynTlHi93ODxEBjaAJG8WFmT7XIn3ro9bLSOUbzEcd7VMf2BbI5Pnp4jpaGkbJIB1z00LY+LLWPyiRjoNb8IoOBp3dxLyCDIW2Ep2UiOPpXUIDJsllX4dUokZ1fRw4MXkysQsZr7P7S93rsPP2vxQRbEoXsmNj+n3o+a+W39kAbbPelPjlQOQozlg7pyBREo1Npu6YTQA9pLz8U2zvfhQaDErlZtPf9N4Kcf3bI2huREhbHgtm/2y1nyKyLUl97p+J5JeWNYPOHo7Xy4jVcPXRySYfYVt7flmVdw4J14OB7yJXGfMSr+0tB2n2cBcIwJY/UdO0YEAfkzPvFfSkCMjLJu7a14/q/DWpDOfpPzPnOkB7Td24eKdudXrXOX/XjGZijbY7s2x220qeAWSPUuBU9ZzhK06cpMHMXJdE2Y46tLTjhrfwpbAcbgGhV1se0lvxRwr4vyh5b/D8+4yQhInYGMn8LAUkCPugU= ahmed@ahmed-pc" >> /home/vagrant/.ssh/authorized_keys
            SHELL
        end
    end
end