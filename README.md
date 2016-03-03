# virtualbox_config_shared_folder_osx

# How to share folder between OSX (HOST) and your virtual machine (GUEST)

0. in HOST, in virtual box VM settings, add the shared HOST folders: devices -> shared folders

   Check auto-mount and permanent

1. in HOST, create optical drive in your VM (machine->settings->storage)
2. in HOST, in virtualbox VM settings: click devices->Insert Guest Additions CD images
   this should tell you that the iso file is there: /Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso

3. in HOST, in VM settings, mount the iso in the VM optical drive
4. in the VM GUEST, mount the iso: `sudo mkdir /media/cdrom;sudo mount /dev/sr0 /media/cdrom`
5. in the VM GUEST, add your user to group vboxsf : `sudo usermod -a -G vboxsf <username>`

6. if in step 0] you didn't check 'auto-mount, in VM GUEST, you can mount manually your shared folders with command:

    `sudo mount -t vboxsf -o uid=1000,gid=1000 <name-of-folder-name> ~/share`
