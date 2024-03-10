# eagle-development-environment

![Eagle Developer](https://imgur.com/jtczs2f.jpg)

This repository contains the configuration of the Eagle Enterprises Development Environment used for building UAV Simulation and Training Environments.

If there is anything wrong with this repository (documentation needed / broken things), please use the [Bug Template](https://github.com/Cybower/eagle-development-environment/issues/new?assignees=&labels=bug&projects=&template=bug-template.md&title=) to report the issue

## Dependencies

### **This is mandatory to set up the Development Environment**

- [Vagrant](https://developer.hashicorp.com/vagrant/downloads): 2.4.1

  After installing vagrant, restart the device, then install these vagrant plugins:

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
   3. For example, one machine was ready after the terminal showed the following message:

      _VirtualBox Guest Additions: Building the modules for kernel 6.5.0-21-generic.
      update-initramfs: Generating /boot/initrd.img-6.5.0-21-generic
      VirtualBox Guest Additions: Running kernel modules will not be replaced until
      the system is restarted or 'rcvboxadd reload' triggered
      VirtualBox Guest Additions: reloading kernel modules and services
      VirtualBox Guest Additions: kernel modules and services 7.0.14 r161095 reloaded
      VirtualBox Guest Additions: NOTE: you may still consider to re-login if some
      user session specific services (Shared Clipboard, Drag and Drop, Seamless or
      Guest Screen Resize) were not restarted automatically_

5. Bring up the VirtualBox UI and click the `eagle-development-environment` VM.
6. Login to the Virtual Machine
   1. uname: `vagrant`
   2. password: `vagrant`

**Note** You can alter the vb.memory value in the Vagrantfile based on how much RAM your personal machine has. I wouldn't give it more than %50 of what your system max is

## VM Usage Guide

1. To start the machine run the following command from within the directory of this cloned repository (i.e. `/eagle-development-environment/`):
   `vagrant up`
2. To open Mission Planner:
3. Open the Terminal
4. Click on the "Show Apps" (grid) button on the lower left corner, which will display the apps menu.
5. Use the search bar at the top to search for "Terminal".
6. Click on the resulting option.
7. Type in /opt/MissionPlanner/MissionPlanner.exe into the terminal.
8. To shutdown the virtual machine, run the following command on a new terminal in VS Code: `vagrant halt`. Virtual Box should show the machine in a "Powered Off" state.

## Git Guide

### Git Useful Commands

`git clone <url>` -------------------- Clones a git repository. URL can be found by clicking the green code button on the repository webpage

`git status` ------------------------- Shows you the status of your local

### Useful Links

- [First Time Git Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)
- [GitHub Skills Page](https://skills.github.com/)
- [The Odin Project](https://www.theodinproject.com/lessons/foundations-introduction-to-git)
- [Learning Git Branching](https://learngitbranching.js.org/)

## Vagrant Guide

### [Documentation](https://developer.hashicorp.com/vagrant/docs)

### Vagrant Useful Commands

`vagrant up` -------------------------------- Brings up the Virtual Machine according to the Vagrantfile in the Working Directory

`vagrant ssh` ------------------------------- Secure Shell into the Virtual Machine

`vagrant halt` ------------------------------ Brings down the Virtual Machine according to the Vagrantfile in the Working Directory **DO THIS BEFORE SHUTTING DOWN YOUR MACHINE**

`vagrant reload` ---------------------------- Will reload the Virtual Machine ( can pass it `--provision` or `--no provision` to force it to be provisioned, which means it will install all dependencies)

`vagrant destroy` --------------------------- Will destroy the Virtual Machine to be brought up with another `vagrant up` **Any work not saved in the `/vagrant` directory will be lost**

## VS Code Extensions

_This is completely optional, just if you're curious as to which I'm using_

- In Bash:
  `cat vs-code-extensions-list.txt | xargs -L 1 code --install-extension`

- In PowerShell:
  `Get-Content vs-code-extensions-list.txt | ForEach-Object { code --install-extension $\_ }`

## Using Mission Planner in the VM

- To open Mission Planner in the VM use the following command:
  `sudo mono /opt/MissionPlanner/MissionPlanner.exe`

## Troubleshooting Guide

### Does VirtualBox work in M1 Macs?

- It has been found that VirtualBox does not operate correctly in Mac PCs with an M1 chip. For more information please visit this [Reddit Thread](https://www.reddit.com/r/mac/comments/14rics9/does_virtualbox_work_in_m1_macs/).

### Error: You need to fork this repository

- If an error occurs in GitHub or in your code editor such as "_Sorry, you're not able to edit this repository directly -- You need to fork it and propose changes from there instead_", please ask access to the repository by sending a direct message via Discord to the repository owner. Once access has been granted by the owner, an email will be sent with an invitation to email linked to your GitHub account. Please click the "Accept Invitation" button on the email. This should resolve the issue.

### Vagrant is not working

- If you just installed Vagrant, the device on which it was installed will need to be restarted before the software is usable.
- Otherwise, please repair vagrant by opening the installer and clicking "Next" > "Repair".
- You can also try to reinstall vagrant

### Vagrant up is taking forever or not working

- The time that the vagrant takes to build the box is heavily dependent on your machine's hardware. It can definitely take much longer than expected.
- Make sure your machine has at least 4 MB available of RAM (memory) to provide to the Box. If your machine has less than that, modify the vagrant file vb.memory value to be less than 50% of your machine's RAM.

### Virtual Box display seems pixelated/flickering/fuzz/static

- For windows, follow these [instructions](https://superuser.com/questions/894328/virtualbox-guests-are-upsampled-blurry-due-to-dpi-scaling-from-windows-host-a). You may need to click aditionally on "Change high DPI settings". Then, shut down the VM as per the VM Usage Guide and restart VirtualBox.

### Mission Planner does not start up/has errors

- Ensure the VM has at least 4 processors.
  - Make sure the VM is off.
  - Go to VBox and select the "Settings" of the VM.
  - Go to System > Processor.
  - Change the number of processors to a more appropriate number.

## Q & A

### How does the repository connect to the VM?

- To get any repos into the VM, please clone them in the `/eagle-development-environment` directory corresponding to this repository on your host system (where the vagrant file is). The repository directories copied there will be bidirectionally synced to the VM.

### Is the developer environment a shared environment or hosted only locally on my machine?

- The developer environment VM is local to each host device.
