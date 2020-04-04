# grmlcustomize
These are some simple scripts that customize the [Grml Linux](https://www.grml.org) 
distribution ISO images. Grml is an extremely nice rescue Linux image, even
without any customization. A particularly cool feature is that the ISO images
can equally serve as dd-able data that you can just put on a USB stick and they
just work. I've not seen that anywhere else and it's an *amazing* feature, this
is so useful and cool. The folks at Grml really know their stuff.

Anyways, this script first loop-mounts the ISO image, then unpacks the
contained squashfs file system, executes some customization hooks and repacks
the SquashFS and ISO.

## Usage
It's pretty straightforward. The help page should explain things:

```
$ ./grmlcustomize --help
usage: grmlcustomize [-h] [-c dirname] [-p {gzip,xz}] [-k dirname]
                     [-t dirname] [-w] [-v]
                     in_iso out_iso

positional arguments:
  in_iso                Unmodified original GRML ISO input image
  out_iso               Customized GRML ISO output image

optional arguments:
  -h, --help            show this help message and exit
  -c dirname, --config-dir dirname
                        Gives the configuration directory that is passed to
                        hooks. Defaults to config.
  -p {gzip,xz}, --compression {gzip,xz}
                        Compression to use for SquashFS. gzip is fast, but
                        creates larger images than xz. Defaults to gzip,
                        choices are gzip, xz.
  -k dirname, --hooks dirname
                        Directory in which customization hooks are kept.
                        Defaults to hooks.
  -t dirname, --tempdir dirname
                        Directory in which temporary files are unpacked.
                        Defaults to /tmp.
  -w, --wait            After applying all hooks, pause for the user to
                        manually change the root tree as they see fit.
  -v, --verbose         Print more verbose information at each step. Can be
                        specified more than once.
```

To run it, you need to execute grmlcustomize as root, however:

```
# ./grmlcustomize grml96-full_2018.12.iso my_own_grml.iso
Parallel unsquashfs: Using 12 processors
69072 inodes (74012 blocks) to write
[...]
created 63191 files
created 7339 directories
created 5831 symlinks
created 7 devices
created 0 fifos
Cloning into 'jbin'...
remote: Enumerating objects: 43, done.
remote: Counting objects: 100% (43/43), done.
remote: Compressing objects: 100% (33/33), done.
remote: Total 195 (delta 20), reused 30 (delta 10), pack-reused 152
Receiving objects: 100% (195/195), 95.64 KiB | 844.00 KiB/s, done.
Resolving deltas: 100% (93/93), done.
Installing ssh public key /home/joe/grmlcustomize/config/ssh-keys/joe.pub
Installing ssh public key /home/joe/grmlcustomize/config/ssh-keys/root.pub
Parallel mksquashfs: Using 12 processors
[...]
xorriso : UPDATE : 1010 files added in 1 seconds
xorriso : NOTE : Copying to System Area: 432 bytes from file '/tmp/grml_07gevqdf/rootfs/usr/lib/ISOLINUX/isohdpfx.bin'
libisofs: NOTE : Automatically adjusted MBR geometry to 1018/92/32
libisofs: NOTE : Aligned image size to cylinder size by 216 blocks
xorriso : UPDATE :  8.87% done
ISO image produced: 749248 sectors
Written to medium : 749248 sectors at LBA 0
Writing to 'stdio:my_own_grml.iso' completed successfully.
```

## Dependencies
grmlcustomize needs a base Grml image, Python3 and xorriso.

## Thanks
Grml is amazing. This is just boilerplate code, all the hard work was done by
them. [Go check it out!](https://www.grml.org)

## License
GNU GPL-3.
