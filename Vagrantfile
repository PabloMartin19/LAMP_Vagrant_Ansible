Vagrant.configure("2") do |config|

    config.vm.define :router do |router|
      router.vm.box = "debian/bookworm64" 
      router.vm.hostname = "router" 
      router.vm.synced_folder ".", "/vagrant", disabled: true
      router.vm.network :public_network,
        :dev => "br0",
        :mode => "bridge",
        :type => "bridge" 
      router.vm.network :private_network,
        :libvirt__network_name => "red_intra",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.10",
        :libvirt__forward_mode => "veryisolated" 
    end

    config.vm.define :web do |web|
      web.vm.box = "debian/bookworm64" 
      web.vm.hostname = "web" 
      web.vm.synced_folder ".", "/vagrant", disabled: true
      web.vm.network :private_network,
        :libvirt__network_name => "red_intra",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.20",
        :libvirt__forward_mode => "veryisolated" 
      web.vm.network :private_network,
        :libvirt__network_name => "red_datos",
        :libvirt__dhcp_enabled => false,
        :ip => "20.0.0.20",
        :libvirt__forward_mode => "veryisolated" 
    end

    config.vm.define :bd do |bd|
      bd.vm.box = "debian/bookworm64" 
      bd.vm.hostname = "bd" 
      bd.vm.synced_folder ".", "/vagrant", disabled: true
      bd.vm.network :private_network,
        :libvirt__network_name => "red_intra",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.30",
        :libvirt__forward_mode => "veryisolated" 
      bd.vm.network :private_network,
        :libvirt__network_name => "red_datos",
        :libvirt__dhcp_enabled => false,
        :ip => "20.0.0.30",
        :libvirt__forward_mode => "veryisolated" 
    end

    config.vm.define :san do |san|
      san.vm.box = "debian/bookworm64" 
      san.vm.hostname = "san" 
      san.vm.synced_folder ".", "/vagrant", disabled: true
      san.vm.network :private_network,
        :libvirt__network_name => "red_intra",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.40",
        :libvirt__forward_mode => "veryisolated" 
      san.vm.network :private_network,
        :libvirt__network_name => "red_datos",
        :libvirt__dhcp_enabled => false,
        :ip => "20.0.0.40",
        :libvirt__forward_mode => "veryisolated" 
      san.vm.provider :libvirt do |libvirt|
        libvirt.storage :file, :size => '2G'
        libvirt.storage :file, :size => '2G'
        libvirt.storage :file, :size => '2G'
      end
    end
  
    config.vm.define :cliente do |cliente|
      cliente.vm.box = "debian/bookworm64"
      cliente.vm.hostname = "cliente"
      cliente.vm.synced_folder ".", "/vagrant", disabled: true
      cliente.vm.network :private_network,
        :libvirt__network_name => "red_intra",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.50", 
        :libvirt__forward_mode => "veryisolated"
    end
  
  end
