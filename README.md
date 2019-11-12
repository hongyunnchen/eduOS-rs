# eduOS-rs - A teaching operating system written in Rust

[![Build Status](https://dev.azure.com/RWTH-OS/eduOS-rs/_apis/build/status/RWTH-OS.eduOS-rs?branchName=stage0)](https://dev.azure.com/RWTH-OS/eduOS-rs/_build/latest?definitionId=1&branchName=stage0)

## Introduction

eduOS-rs is a Unix-like operating system based on a monolithic architecture for educational purposes.
It is developed for the course [Operating Systems][acsos] at RWTH Aachen University and supports x86 and aarch64 processors (thanks to Leonard Rapp).
eduOS-rs is derived from following tutorials and software distributions:

1. Philipp Oppermann's [excellent series of blog posts][opp].
2. Erik Kidd's [toyos-rs][kidd], which is an extension of Philipp Opermann's kernel.
3. The original version of [eduOS][stlankes], which was the old teaching kernel written in C.

[opp]: http://blog.phil-opp.com/
[kidd]: http://www.randomhacks.net/bare-metal-rust/
[stlankes]: http://rwth-os.github.io/eduOS/
[rust-barebones-kernel]: https://github.com/thepowersgang/rust-barebones-kernel
[acsos]: http://www.os.rwth-aachen.de/

## Requirements to build eduOS-rs
eduOS-rs is tested under Linux, macOS, and Windows.

### macOS
Apple's *Command Line Tools* must be installed.
The Command Line Tool package gives macOS terminal users many commonly used tools and compilers, that are usually found in default Linux installations.
Following terminal command installs these tools without Apple's IDE Xcode:

```sh
$ xcode-select --install
```

It is also recommended to install the packet manager [Homebrew](https://brew.sh).
eduOS-rs depends on [Qemu](https://www.qemu.org/), which is a open source machine emulator.
Please use Homebrew to install Qemu as follows:

```sh
$ brew install qemu
```

### Windows
To build eduOS-rs you have to install a linker, the tool [make](http://gnuwin32.sourceforge.net/packages/make.htm), a [git client](https://git-scm.com/downloads) and the emulator [Qemu](https://www.qemu.org/).
We tested eduOS-rs with the linker from Visual Studio.
Consequently, we suggest to install Visual Studio.
Please install also the packet manager [Chocolatey](https://chocolatey.org) and use it to install the packages for _make_ and _git_.

```sh
$ choco install qemu make
```

### Linux
Linux users should install common developer tools.
For instance, on Ubuntu 18.04 the following command installs the required tools:

```sh
$ apt-get install -y curl wget qemu-system-x86 nasm make autotools-dev gcc g++ build-essential
```

### Common for macOS, Windows and Linux
It is required to install the Rust toolchain.
Please visit the [Rust website](https://www.rust-lang.org/) and follow the installation instructions for your operating system.
It is important that the *nightly channel* is used to install the toolchain.
This is queried during installation and should be answered as appropriate.

Afterwards the installation of *cargo-xbuild* and the source code of Rust runtime are required to build the kernel:

```sh
$ cargo install cargo-xbuild
$ rustup component add rust-src
$ rustup component add llvm-tools-preview
```

It is also recommended to install [bootimage](https://github.com/rust-osdev/bootimage) to build a bootable image.

```sh
$ cargo install bootimage
```


## Building
The final step is to create a copy of the repository and to build the kernel:

```sh
$ # Get our source code.
$ git clone https://github.com/RWTH-OS/eduOS-rs.git
$ cd eduOS-rs

$ # Build kernel
$ make
```

From here, we should be able to run the kernel in Qemu:

```sh
$ make qemu
```

## Overview of all branches

Step by step (here branch by branch) the operating system design will be introduced.
This tutorial shows the steps to develop from a minimal kernel to a Unix-like computer operating system.
Currently, following stages of development are available:

0. stage0 - Smallest HelloWorld of the World

   Description of loading a minimal 64bit kernel

## Useful Links

1. [http://www.gnu.org/software/grub/manual/multiboot/](http://www.gnu.org/software/grub/manual/multiboot/)
2. [http://www.osdever.net/tutorials/view/brans-kernel-development-tutorial](http://www.osdever.net/tutorials/view/brans-kernel-development-tutorial)
3. [http://www.jamesmolloy.co.uk/tutorial_html/index.html](http://www.jamesmolloy.co.uk/tutorial_html/index.html)
4. [http://techblog.lankes.org/tutorials/](http://techblog.lankes.org/tutorials/)
5. [http://www.os.rwth-aachen.de](http://www.os.rwth-aachen.de)
6. [http://www.noteblok.net/2014/06/14/bachelor](http://www.noteblok.net/2014/06/14/bachelor)
7. [https://sourceware.org/newlib/](https://sourceware.org/newlib/)
8. [http://rwth-os.github.io/eduOS/](http://rwth-os.github.io/eduOS/)
9. [https://intermezzos.github.io](https://intermezzos.github.io)

## License

Licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.
