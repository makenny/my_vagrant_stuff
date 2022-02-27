# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Box
  config.vm.box = "StefanScherer/windows_2019"

  # Additional parameters to communicate with Windows
  config.vm.boot_timeout = 60
  config.vm.communicator = "winrm"
  config.winrm.port = 55985

  # Customization
  config.vm.provider "vmware_desktop" do |v|
    v.gui = true
    v.memory = 1024
    v.vmx["displayName"] = "win2019"
    v.vmx["memsize"] = "1024"
    v.vmx["numvcpus"] = "2"
  end
  config.vm.network :forwarded_port, guest: 80, host: 8080, id: "http"

  # Provisioning
  config.vm.provision "shell", path: "scripts/InstallChocolatey.ps1"
  config.vm.provision "shell", inline: "choco install vscode --yes"

end
