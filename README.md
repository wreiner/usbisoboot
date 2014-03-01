usbisoboot
==========

<p>Booting multiple ISOs from an USB stick using Grub</p>

<p>Based on the information found at [http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)</p>
1. Create a partition on the usb stick (partition type 0x0C)
2. Create filesystem on the partition
<pre><code>mkfs.vfat -n isostick /dev/sdX1</pre></code>
3. Mount the filesystem
<pre><code>mount /dev/sdX1 /mnt/isostick</pre></code>
4. Install grub2 on usb drive
<pre><code>grub-install --no-floppy --recheck --root-directory=/mnt /dev/sdX</pre></code>
5. Create the directory structure
<pre><code>mkdir -p /mnt/boot/{group,iso}</pre></code>
6. Copy the file grub/grub.cfg onto the stick
<pre><code>cp grub.cfg /mnt/isostick/boot/grub/grub.cfg</pre></code>
7. Copy all needed iso files on the stick
<pre><code>rsync --progress <whatever>.iso /mnt/isostick/boot/iso</pre></code>
8. Create the corresponding menuentry
<pre><code>some of the usual ones can already be found in the grub.cfg</pre></code>
9. Unmount and enjoy

<p>If you have additional configurations, please file a pull request for them.</p>
