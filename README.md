# eagle-development-environment

![Eagle Developer](https://imgur.com/jtczs2f.jpg)

This repository contains the configuration of the Eagle Enterprises Development Environment used for building UAV Simulation and Training Environments.

If there is anything wrong with this repository (documentation needed / broken things), please use the [Bug Template](https://github.com/Cybower/eagle-development-environment/issues/new?assignees=&labels=bug&projects=&template=bug-template.md&title=) to report the issue

## Dependencies

### **This is mandatory to set up the Development Environment**

- [Vagrant](https://developer.hashicorp.com/vagrant/downloads): 2.4.1
  - vagrant-hostmanager
    - `vagrant install vagrant-hostmanager`
  - vagrant-vboxguest
    - `vagrant plugin install vagrant-vbguest`
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads): 7.0.8
  - [Virtual Box Oracle VM VirtualBox Extension Pack](https://download.virtualbox.org/virtualbox/7.0.14/Oracle_VM_VirtualBox_Extension_Pack-7.0.14.vbox-extpack)
- [git](https://git-scm.com/downloads): version 2.41.0.windows.2
- Integrated Development Environment (_of your choice_)
  - [VSCode](https://code.visualstudio.com/download) (_Adam's personal favorite; I have workspace settings and my extensions that I used included_ )
  - [Eclipse](https://www.eclipse.org/downloads/)
  - [JetBrains](https://www.jetbrains.com/products/)
  - [Notepad++](https://notepad-plus-plus.org/downloads/) (_If you're looking for a challenge_)
  - [VIM](https://www.vim.org/download.php) (_If you're a masochist_)

## Set Up Guide

1. Install Dependencies Listed Above
2. Clone this repository to a folder on your personal computer
3. Run the following command from within the cloned repository (i.e. `/eagle-development-environment/`):
   `vagrant up`
4. Wait for the Vagrant Command to bring up the Virtual Machine
   1. It may take a few minutes, depending on your machine and internet connectivity
   2. Time snapshot of mine
      1. real 2m32.230s
      2. user 0m0.000s
      3. sys 0m0.016s
5. Bring up the VirtualBox UI and Show the `eagle-development-environment`
6. Login to the Virtual Machine
   1. uname: `vagrant`
   2. password: `vagrant`

**Note** You can alter the vb.memory value in the Vagrantfile based on how much RAM your personal machine has. I wouldn't give it more than %50 of what your system max is

## Vagrant Guide

### [Documentation](https://developer.hashicorp.com/vagrant/docs)

### Useful Commands

`vagrant up` -------------------------------- Brings up the Virtual Machine according to the Vagrantfile in the Working Directory

`vagrant ssh` ------------------------------- Secure Shell into the Virtual Machine

`vagrant halt` ------------------------------ Brings down the Virtual Machine according to the Vagrantfile in the Working Directory **DO THIS BEFORE SHUTTING DOWN YOUR MACHINE**

`vagrant reload` ---------------------------- Will reload the Virtual Machine ( can pass it `--provision` or `--no provision` to force it to be provisioned, which means it will install all dependencies)

`vagrant destroy` --------------------------- Will destroy the Virtual Machine to be brought up with another `vagrant up` **Any work not saved in the `/vagrant` directory will be lost**

## VS Code Extensions

- _This is completely optional, just if you're curious as to which I'm using_

- In Bash:
  `cat vs-code-extensions-list.txt | xargs -L 1 code --install-extension`

- In PowerShell:
  `Get-Content vs-code-extensions-list.txt | ForEach-Object { code --install-extension $\_ }`
