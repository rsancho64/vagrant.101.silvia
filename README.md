Hacemos [**este**](https://dev.to/carltonupp/vagrant-101-35pj) curso

Vagrant is a **lightweight dev-envs** tool.

As someone that likes to experiment (languages/tecnologies), it can often be a massive pain to get **local dev-envs** set up before jumping into a new project.

... the dependencies hell ... the settings hell ... 

Tools like Vagrant exist to make this process much easier. Once again, the idea is a tiny VM fully configured. Changes only last as long as the VM exists and they don't pollute the host machine w unused runtimes and SDKs.

Vagrant: *ability to define a complete dev-env within a single, human-readable file*. This file can be kept in the project's repo so any time you need to do further work, you can simply spin up the dev-env and get to work.

- [x] 1. [instalo](https://developer.hashicorp.com/vagrant/install#linux) Vagrant 

```sh
sudo su # ...
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install vagrant
whereis vagrant # > vagrant: /usr/bin/vagrant /opt/vagrant/bin/vagrant
```

- [ ] 2. Creo un Vagrant env using the `hashicorp/bionic64` box

box ~ base image for a vm, usually defining the underlying os and eventual installed runtimes.

boxes at **[Vagrant Cloud](https://app.vagrantup.com/boxes/search)**, or alternatively created by us.

```sh
vagrant init  # new Vagrantfile
```sh

```rb
Vagrant.configure("2") do |config|
  config.vm.box = "base"
end
```

```sh
vagrant up
The provider 'virtualbox' that was requested to back the machine 'default' 
is reporting that it isn't usable on this system. The reason is shown below:

Vagrant could not detect VirtualBox! Make sure VirtualBox is properly installed.
Vagrant uses the `VBoxManage` binary that ships with VirtualBox, and requires
this to be available on the PATH. If VirtualBox is installed, please find the
`VBoxManage` binary and add it to the PATH environmental variable.
```

Vagrant precisa un hipervisor. Pude ser Virtual Box u otro, pero lo necesita por debajo.
Ver [esto](https://tecnolitas.com/blog/laboratorio-multi-maquina-con-vagrant/) 

- [ ] VER: https://github.com/ppggff/vagrant-qemu
- [ ] VER: k (Windows VM on Linux using QEMU/kvm/VirtIO // Ditch Your VirtualBox!)

No VirtualBox en ubuntu 23.10 ? Pues Mejor.
Ver [QEMU/KVM stack with Virt-manager as GUI](https://askubuntu.com/questions/1491265/ubuntu-23-10-no-virtualbox-available-what-can-be-done)

[howto-install-qemu-on-ubuntu-23-10](https://askubuntu.com/questions/1490805/how-do-i-install-qemu-on-ubuntu-23-10)

QEMU: quoting [https://www.qemu.org/download/#linux](https://www.qemu.org/download/#linux) 
- For full system emulation run: `apt-get install qemu-system`
- For emulating Linux binaries run: `apt-get install qemu-user-static`

- [ ] 3. inicio la máquina virtual --> vagrant up
- [ ] 4. conexión a la máquina virtual--> vagrant ssh
- [ ] 5. creo un holamundo en un editor de texto nano

sudo apt install 
qemu -> qemu-system
qemu-kvm -> 
libvirt-daemon 
libvirt-daemon-system 
libvirt-clients 
bridge-utils
