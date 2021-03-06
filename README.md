# Vagrant-Kali with Shared Folder Auto-Mount

![Kali Linux](https://www.kali.org/) as a ![Vagrant](https://www.vagrantup.com/) box: all the persistance of bare metal with the convenience of a live USB.

* Uses the [official `offensive-security/kali-linux` Vagrant box](https://www.kali.org/news/announcing-kali-for-vagrant/) as the base box.
* Mounts the current directory into the VM as a shared folder at `/vagrant/`. Sync more folders at will.
* Vagrant auto-NATs the VM with the host machine: networking should be automagic.

Currently requires ![VirtualBox](https://virtualbox.org)

## Usage

### OPTIONAL: Setting Up SSHFS as auto shared folder

Install SSHFS support for auto shared folder `vagrant plugin install vagrant-sshfs`

[Optional] -- If having issues with too many keys in ssh-agent i.e SSHFS mount fails, too many keys in agent
in your ssh-config..

```
Host 127.0.0.1
  AddKeysToAgent no
```

### How to start this vagrant box

```console
# Auto-build the VM
$vagrant up

# Get a shell into the VM
$vagrant ssh

# Suspend the VM
$vagrant halt

# Delete the VM
$vagrant destroy

# Some other helpful commands

# Reconfigure the virtual machine after a source code change.
$vagrant provision

# Reload the virtual machine. Useful when you need to change network or synced folder settings.
$vagrant reload



```
* I keep my vagrantfiles in `~/VagrantMachines` so I recommend cloning this repo there.
* The VM login is vagrant:vagrant (not kali:kali)
* The first pull of the Vagrant box will take a while: Kali is ~4GB.
* Kali's default `root:toor` login/password is still valid. If you really want to be root, `su - root`.
* Updating Kali's full suite of packages with `apt-get upgrade` takes about 30 years on a fresh box, so plan accordingly.
* Line endings of any config files shared to the Vagrant box should have Unix-style/LF line endings.
* VM settings (CPU/RAM allocation, no GUI, etc.) can be changed by modifying the `Vagrantsettings.yaml`.
* The `custom.sh` script can be modified to add packages/custom code.

**NOTE:** Share directory is setup like so `config.vm.synced_folder "~/VagrantMachines/share/", "/share/", type: "sshfs"`

### Screenshots

![screenshot](https://i.ibb.co/VWNWRdm/Screen-Shot-2021-02-27-at-7-57-59-am.png)

**You will also see the full VM in Vbox and can be launched normally from there**

![screenshot](https://i.ibb.co/7K0r97S/Screen-Shot-2021-02-27-at-8-03-53-am.png)

![screenshot](https://i.ibb.co/Z6MY3ZR/Screen-Shot-2021-02-27-at-8-02-37-am.png)

### References
- kali-linux: https://www.kali.org/
- vagrant: https://www.vagrantup.com/
- virtualbox: https://www.virtualbox.org/
