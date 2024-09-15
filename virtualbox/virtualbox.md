# VirtualBox

## Export a VM creating a .ova file

1. Open VirtualBox manager

2. Open the export wizard from to menu item:

   - File > Esporta applicazione virtuale...

3. Select the VM and Choice the export settings

## Compact virtual disk files (.vdi files)

1. Open a shell in the Guest VM as 'root' user

   ```bash
   sudo su
   ```

2. Found the mount path of each virtual-disk to reduce

   ```bash
   df -h
   ```

   ```console
   File system     Dim. Usati Dispon. Uso% Montato su
   ...
   /dev/sda2        98G   34G     60G  37% /
   ...
   /dev/sdb1        98G   36G     58G  38% /home
   /dev/sdc1        98G   27G     67G  29% /var/lib/docker
   ...
   ```

3. Fill freespace with zeros inside each mount path

   ```bash
   dd if=/dev/zero of=/zerofile bs=1M
   rm -f /zerofile
   ```

   ```bash
   dd if=/dev/zero of=/home/zerofile bs=1M
   rm -f /zerofile
   ```

   ```bash
   dd if=/dev/zero of=/var/lib/docker/zerofile bs=1M
   rm -f /zerofile
   ```

4. Shutdown the VM

5. Open a shell in the Host PC as 'administrator' user

   ```ps
   cd "C:\Program Files\Oracle\VirtualBox\"
   ```

6. Execute compact command for each virtual disk files:

   ```ps
   .\VBoxManage.exe modifymedium "C:\VM\VirtualBox\ubuntu\system.vdi" --compact
   .\VBoxManage.exe modifymedium "C:\VM\VirtualBox\ubuntu\home.vdi" --compact
   .\VBoxManage.exe modifymedium "C:\VM\VirtualBox\ubuntu\docker.vdi" --compact
   ```
