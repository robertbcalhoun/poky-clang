# poky

This repository mirrors the official yocto poky repository at
[git://git.yoctoproject.org/poky](git://git.yoctoproject.org/poky)
and contains additional patches to help compile at least the
`core-image-minimal` using clang.

See [meta-tc-llvm](https://github.com/mtahmed/meta-tc-llvm). It's
a secondary toolchain layer which needs to be added to this poky
to help it compile using clang.

## Status

Able to build all the packages for core-image-minimal except the following:

- linux-yocto-tiny
- dtc
- elfutils
- gcc
- gcc-cross
- gcc-cross-initial
- gcc-runtime
- prelink
- eglibc
- rpm
- libgcc
- e2fsprogs

## Installation

Simply clone this repository and add the `meta-tc-llvm` layer.

```bash
git clone https://github.com/mtahmed/poky-clang.git
cd poky
git clone https://github.com/mtahmed/meta-tc-llvm.git
```

All the required patches are already in poky. For configuration
specific to `meta-tc-llvm` layer, see the `meta-tc-llvm` link above.

## Patches

These are the set of patches already included in this poky:

- [busybox: find-get-rid-of-nested-functions.patch](https://github.com/mtahmed/poky/blob/master/meta/recipes-core/busybox/busybox-1.21.1/find-get-rid-of-nested-functions.patch):
  taken from upstream busybox repository
- [ncurses: fix-types-in-constructor-declaration.patch](https://github.com/mtahmed/poky/blob/master/meta/recipes-core/ncurses/ncurses-5.9/fix-types-in-constructor-declaration.patch):
  taken from [http://trac.macports.org/ticket/30312](http://trac.macports.org/ticket/30312)
- [db: atomic.patch](https://github.com/mtahmed/poky/blob/master/meta/recipes-support/db/db/atomic.patch):
  taken from [https://github.com/narkoleptik/os-x-berkeleydb-patch](https://github.com/narkoleptik/os-x-berkeleydb-patch)
- [elfutils: rewrite-nested-functions-and-fix-types.patch](https://github.com/mtahmed/poky/blob/master/meta/recipes-devtools/elfutils/elfutils-0.155/rewrite-nested-functions-and-fix-types.patch):
  adapted for 0.155 from [elfutils-clang-patches](https://github.com/m0use/elfutils-clang-patches)
- [elfutils: replace-variable-length-array-in-structure.patch](https://github.com/mtahmed/poky/blob/master/meta/recipes-devtools/elfutils/elfutils-0.155/replace-variable-length-array-in-structure.patch):
  wrote myself
- [pseudo: remove-non-constant-static-initialiazation.patch](https://github.com/mtahmed/poky/blob/master/meta/recipes-devtools/pseudo/files/remove-non-constant-static-initialization.patch):
  wrote myself


## Contact

- Muhammad Tauqir Ahmad
- muhammad.tauqir.ahmad@gmail.com
- [csclub.uwaterloo.ca/~mtahmed](http://csclub.uwaterloo.ca/~mtahmed)
