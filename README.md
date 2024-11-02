# makevm

Script to create a libvirt VM with a cloud image (cloud-init).

## Requirements

- `libvirt` with `virsh` and `virt-install`
- `sudo` privileges on the hypervisor. The script could probably
do without, but I run it on the hypervisor itself.

## Before using the script

Make `images` and `temp` directories where you cloned the repo.

```
git clone https://github.com/alphanumeric3/makevm.git
cd makevm
mkdir images temp
```

Place QCOW2 images in `images`.

```
cd images
wget https://example.com/cloud-init.qcow2 -O best.qcow2
```

You can also symlink `default.qcow2` to an image to have the script
use it by default.


## Usage

`-n`: VM name (and hostname set through meta-data)
`-m`: Memory in MB
`-s`: Disk size in GB
`-u`: cloud-init user-data file
`-t`: QCOW2 template to use. Must be in the `images` directory.

Example:

```
./makevm -n name -m 1024 -s 20 -u user-data -t template.qcow2
```

Makes "name" with 1GB RAM, 20GB disk and uses the file `user-data` and
the template `images/template.qcow2`.
