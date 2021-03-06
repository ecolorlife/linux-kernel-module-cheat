# modprobe

If you are feeling fancy, you can also insert modules with:

    modprobe dep2
    lsmod
    # dep and dep2

This method also deals with module dependencies, which we almost don't use to make examples simpler:

- <https://askubuntu.com/questions/20070/whats-the-difference-between-insmod-and-modprobe>
- <https://stackoverflow.com/questions/22891705/whats-the-difference-between-insmod-and-modprobe>

Removal also removes required modules that have zero usage count:

    modprobe -r dep2
    lsmod
    # Nothing.

but it can't know if you actually insmodded them separately or not:

    modprobe dep
    modprobe dep2
    modprobe -r dep2
    # Nothing.

so it is a bit risky.

`modprobe` searches for modules under:

    ls /lib/modules/*/extra/

Kernel modules built from the Linux mainline tree with `CONFIG_SOME_MOD=m`, are automatically available with `modprobe`, e.g.:

    modprobe dummy-irq
