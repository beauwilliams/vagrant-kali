# vagrant-kali

Kali Linux Vagrant box with some usability scripts.

* Uses the [official `offensive-security/kali-linux` Vagrant box](https://www.kali.org/news/announcing-kali-for-vagrant/) as the base box.
* Mounts the current directory into the VM as a shared folder at `/vagrant/` automatically.
* Vagrant auto-NATs the VM with the host machine: networking should be automatic.

### Usage

```console
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'offensive-security/kali-linux' is up to date...
...
$ vagrant ssh
vagrant@kali:~$ su - root
Password:
root@kali:~#
```

* The first pull of the Vagrant box will take a while: Kali is ~4GB.
* Kali's default `root:toor` login/password is still valid. If you really want to be root, `su - root`.
* Updating Kali's full suite of packages with `apt-get upgrade` takes about 30 years on a fresh box, so plan accordingly.
* Line endings of any config files shared to the Vagrant box should have Unix-style/LF line endings.
* VM settings (CPU/RAM allocation, no GUI, etc.) can be changed by modifying the `Vagrantsettings.yaml`.
* The `custom.sh` script can be modified to add packages/custom code.
