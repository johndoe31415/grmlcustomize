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

# Dependencies
grmlcustomize needs a base Grml image, Python3 and xorriso.

# Thanks
Grml is amazing. This is just boilerplate code, all the hard work was done by
them. [Go check it out!](https://www.grml.org)

## License
GNU GPL-3.
