machines = {
  "master" => {"memory" => "512", "cpu" => "1", "ip" => "170"},
  "node01" => {"memory" => "512", "cpu" => "1", "ip" => "171"},
  "node02" => {"memory" => "512", "cpu" => "1", "ip" => "172"}
}

Vagrant.configure("2") do |config|
  machines.each do |name, conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "starboard/ubuntu-arm64-20.04.5"
      config.vm.box_version = "20221120.20.40.0"
      machine.vm.hostname = "#{name}"
      # machine.vm.network "public_network", bridge: "en6: USB 10/100/1000 LAN"
      machine.vm.provider "vmware_desktop" do |vw|
        vw.ssh_info_public = true
        vw.vmx["ethernet0.pcislotnumber"] = "33"
        vw.vmx["ethernet0.virtualdev"] = "vmxnet3"
        vw.gui = true
        vw.linked_clone = false
        vw.memory = conf["memory"]
        vw.cpus = conf["cpu"]
      end
    end
  end
end




# Vagrant.configure("2") do |config|
#   config.vm.box = "starboard/ubuntu-arm64-20.04.5"
#   config.vm.box_version = "20221120.20.40.0"
#   config.vm.box_download_insecure = true
#   config.vm.network "public_network", ip: "172.16.41.170"
#   config.vm.provider "vmware_desktop" do |v|
#     v.ssh_info_public = true
#     v.vmx["ethernet0.pcislotnumber"] = "33"
#     v.vmx["ethernet0.virtualdev"] = "vmxnet3"
#     v.gui = true
#     v.memory = "768"
#     v.linked_clone = false
#   end
# end
