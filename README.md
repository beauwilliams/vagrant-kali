# vagrant-kali

Kali Linux Vagrant box with some usability scripts.

* The [official `offensive-security/kali-linux` Vagrant box](https://www.kali.org/news/announcing-kali-for-vagrant/) is used as the base box.
* By default, the current directory is mounted into the VM as a shared folder at `/vagrant/`.
* Kali's default `root:toor` login is still valid.

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

* Updating Kali's full set of packages with `apt-get upgrade` usually takes about 30 years. Plan accordingly.
* Line endings of any config files shared to the Vagrant box should have Unix-style/LF line endings.
* VM settings can be changed by modifying the `Vagrantsettings.yaml`,
* The `custom.sh` script can be modified to add packages/custom code.
