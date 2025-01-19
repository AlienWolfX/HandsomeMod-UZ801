<h1 align="center">HandsomeMod 21.03</h1>
<h4 align="center">IOT Freedom For End-user!</h4>

## Building Firmware

> [!NOTE]
> Some packages makefiles have been modified to work with my local apache server.
> Built on **Ubuntu 20.04**

To build your own firmware you need a Linux, BSD or MacOSX system (case
sensitive filesystem required). Cygwin is unsupported.

You need gcc, binutils, bzip2, flex, python, perl, make, find, grep, diff,
unzip, gawk, getopt, subversion, libz-dev and libc headers installed.

1. Run "./scripts/feeds update -a" to obtain all the latest package definitions
defined in feeds.conf / feeds.conf.default

2. Run "./scripts/feeds install -a" to install symlinks for all obtained
packages into package/feeds/ 

3. Run "make menuconfig" to select your preferred configuration for the
toolchain, target system & firmware packages.

4. Run "make" to build your firmware. This will download all sources, build
the cross-compile toolchain and then cross-compile the Linux kernel & all
chosen applications for your target system.

> [!CAUTION]
> This SDK is unstable; firmware produced with it should be treated with caution.

## License

HandsomeMod is licensed under GPL-2.0

