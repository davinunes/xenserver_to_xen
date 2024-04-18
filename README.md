xenserver_to_xen
================
  This project is for migrating from xenserver `*.xva` image to xen `*.img` image.

### Quickstart
1. Untar your xenserver image {{image}} with the command: `tar -xvf {image}.xva`. There are Ref:XX folder and ova.xml, where Ref:XX which contains 1MB size chunks of the image disk and ova.xml represents image spec.

2. Then grab this handy utility and run it on your untared data, as an example:
>    python xenmigrate.py –-convert=Ref:XX {image}.img

3. If you'd like to convert `{image}.img` to `{image}.qcow2`, you can run the command:
>    qemu-img convert -f raw -O qcow2 {image}.img {image}.qcow2
>

### Comandos rápidos

```
wget https://raw.githubusercontent.com/davinunes/xenserver_to_xen/master/xenmigrate.py

    mkdir blue
    tar -xvf  blueiris.xva -C blue/
    ll
    ll
    rm blueiris.xva
    cd blue/
    ll
    qm disk import  103 bluiris_disco1.img LVM-2T
    ll
    python3 /opt/xenmigrate.py --convert=Ref:180 bluiris_disco1.img
    python3 /opt/xenmigrate.py --convert=Ref:177 bluiris_disco0.img
    ll
    rm -rf Ref:177 Ref:180
    ll
    rm ova.xml
    qm disk import  103 bluiris_disco1.img LVM-2T
    qm disk import  103 bluiris_disco0.img LVM-2T
    ll
    rm bluiris_disco0.img bluiris_disco1.img
```
