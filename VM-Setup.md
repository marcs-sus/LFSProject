# Virtual Machine Setup

## Requirements for the Virtual Machine

- [Oracle VirtualBox](https://www.virtualbox.org/)
- [Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist)
- [Arch Linux Disc Image file](https://archlinux.org/download/)
- Enable Hardware Virtualization on machine BIOS

> Set up the Virtual Machine with the desired hardware, and allocate the ISO via Settings

## Arch linux Installation Steps

- Use `ping` command to verify internet connection
- Use `pacman -Sy` to synchronize with package databases
- Use `pacman -S` to install `archlinux-keyring` and `archinstall` packages:
  - `pacman -S archlinux-keyring`
  - `pacman -S archinstall`
- Use `archinstall` command to procede to the Arch Linux Installation
  - On Disk configuration, select the default partition layout
  - On Swap, enable
  - On Bootloader, use Grub
  - On Root password, create a password
  - On User account, create an user, ensure that superuser (`sudo`) is enabled
  - On Profile, select Desktop, and the desired environment package (GNOME is preferable)
    - On Graphics driver, select all open-source
  - On Audio, use pipewire
  - On Kernels, you may install additional kernels, if so desired
  - On Network configuration, use NetworkManager
  - On Additional Packages, you may install optional packages, separated by spaces
    - `git fastfetch htop` and others are commonly used
  - On Timezone, select the appropriate timezone
- After configuring all the options select Install to perform the OS Installation
  - This process may take some minutes
- Use `exit` the CHROOT, and `shutdown now` to shut down the VM

> Remove the associated ISO file of the VM to boot Arch Linux next!

### VirtualBox Guest Additions (Optional)

- When booting Arch Linux, open the Console
- Use `sudo pacman -Syyu` to synchronize databases
- Use `sudo pacman -S base-devel linux-headers` for kernel headers
- On the VirtualBox Devices menu, select Insert Guest Additions CD image...
- Open the files, and copy all files from the VBox virtual CD to the Documents folder
- Open the Console, `cd Documents` and `sudo chmod 777 VBoxLinuxAdditions.run` to add permissions
  - Then run the file `sudo ./VBoxLinuxAdditions.run`
