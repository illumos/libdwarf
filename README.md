# libdwarf

This repository contains the versions of libdwarf that are used in
illumos. Each release of libdwarf that we import from
https://www.prevanders.net/dwarf.html is present as a branch in this
repository whose name matches the date. For example, the release
libdwarf-20191104.tar.gz would be illumos/20191104. The branch contains
a base commit, which is the release tarball. From there, changes that we
have applied to build on illumos are committed as individual patches.

## Updating libdwarf

To update libdwarf in illumos, you should first grab the most recent
tarball and figure out which of the patches still apply. After that, you
will need to copy the contents of the `libdwarf` directory to
`usr/src/common/lib/libdwarf`. You will need to manually update the
following:

1. The illumos makefiles to have an accurate list of objects
2. The illumos mapfile to refer to new symbols
3. Manually diff the generated `config.h` to make sure that new options
are properly accounted for and that the `config.h` in the tree properly
accounts for SPARC vs. x86 (currently this is in the endian macros).

Once you have something that is working and tested in illumos, you
should create a new branch in this repository based on the date. The
base commit should be the new version of libdwarf. Afterwards, any
changes that you have made to the build should be incremental commits on
top of this. It is important that the first commit be pristine so it is
obvious what has changed when someone else comes to update this in the
future.
