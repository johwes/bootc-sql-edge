The repo containes an example of creating a bootc container with an embedded container image.
The embeeded container in this example is Azure SQL Edge Container,
https://learn.microsoft.com/en-us/azure/azure-sql-edge/disconnected-deployment

The container image is here,
```
quay.io/jwesterl/bootc-azuresqledge:latest
```

Build using,
```
podman build --cap-add SYS_ADMIN -f Containerfile -t quay.io/jwesterl/bootc-azuresqledge .
```

Installed using the following, modify the paths and make sure you Download the ISO
```
virt-install --connect qemu:///system --name bifrost.home.lab --memory 4096 --vcpus 2 --os-variant fedora-unknown --cdrom /home/jwesterl/Downloads/Fedora-Everything-netinst-x86_64-39-1.5.iso --video virtio --graphics spice --noautoconsole --disk size=10 --initrd-inject=/home/jwesterl/bifrost/bootc-sql-edge/example.ks --extra-args inst.ks=file:/example.ks --location /home/jwesterl/Downloads/Fedora-Everything-netinst-x86_64-39-1.5.iso
```

