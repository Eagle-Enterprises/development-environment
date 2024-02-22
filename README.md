# eagle-development-environment

## Dependencies

### **This is mandatory to set up the Development Environment**

- [Vagrant](https://developer.hashicorp.com/vagrant/downloads): 2.4.1
  - vagrant-hostmanager
    - `vagrant install vagrant-hostmanager`
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads): 7.0.8
- [git](https://git-scm.com/downloads): version 2.41.0.windows.2

## Set Up Guide

1. Install Dependencies Listed Above
2. Clone this repository to a folder on your personal computer
3. Run the following command from within the cloned repository (i.e. `/eagle-development-environment/`):
   `vagrant up`
4. Wait for the Vagrant Command to bring up the Virtual Machine
   1. It will take a considerable amount of time, depending on your machine and internet connectivity

## Vagrant Guide

### [Documentation](https://developer.hashicorp.com/vagrant/docs)

### Useful Commands

`vagrant up` -------------------------------- Brings up the Virtual Machine according to the Vagrantfile in the Working Directory
`vagrant halt` ------------------------------ Brings down the Virtual Machine according to the Vagrantfile in the Working Directory **DO THIS BEFORE SHUTTING DOWN YOUR MACHINE**
`vagrant reload` ---------------------------- Will reload the Virtual Machine ( can pass it `--provision` or `--no provision` to force it to be provisioned, which means it will install all dependencies)
`vagrant destroy` --------------------------- will destroy the Virtual Machine to be brought up with another `vagrant up` **Any work not saved in the `/vagrant` directory will be lost**

## VS Code Extensions

- _This is completely optional, just if you're curious as to which I'm using_

- In Bash:
  `cat vs-code-extensions-list.txt | xargs -L 1 code --install-extension`

- In PowerShell:
  `Get-Content vs-code-extensions-list.txt | ForEach-Object { code --install-extension $\_ }`
