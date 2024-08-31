[ltsc-like](https://github.com/memstechtips/UnattendedWinstall/blob/main/IoT-LTSC-Like/autounattend.xml)

1. Install necessary tools:
   First, ensure you have the required tools installed. Open a terminal and run:

   ```
   sudo apt update
   sudo apt install genisoimage p7zip-full
   ```

2. Create a working directory:
   ```
   mkdir win11_iso_mod
   cd win11_iso_mod
   ```

3. Mount the ISO:
   ```
   sudo mkdir /mnt/win11iso
   sudo mount -o loop path/to/your/windows11.iso /mnt/win11iso
   ```
   Replace "path/to/your/windows11.iso" with the actual path to your ISO file.

4. Copy ISO contents:
   ```
   mkdir iso_contents
   cp -r /mnt/win11iso/* iso_contents/
   ```

5. Unmount the ISO:
   ```
   sudo umount /mnt/win11iso
   ```

6. Add your autounattend.xml:
   ```
   cp path/to/your/autounattend.xml iso_contents/
   ```
   Replace "path/to/your/autounattend.xml" with the actual path to your autounattend.xml file.

7. Recreate the ISO:
   ```
   genisoimage -udf -allow-limited-size -iso-level 3 -b boot/etfsboot.com -no-emul-boot -boot-load-size 8 -hide boot.catalog -eltorito-alt-boot -b efi/microsoft/boot/efisys.bin -no-emul-boot -o win11_modified.iso iso_contents/
   ```

   This command creates a new ISO file named "win11_modified.iso" in your current directory.

8. Clean up:
   ```
   rm -rf iso_contents
   ```

After these steps, you should have a new ISO file named "win11_modified.iso" that includes your autounattend.xml file.

Some important notes:
- Ensure you have enough disk space to work with the ISO contents.
- The exact parameters for the genisoimage command might need adjustment depending on the specific structure of your Windows 11 ISO.