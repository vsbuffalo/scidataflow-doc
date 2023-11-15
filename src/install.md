# Installing SciDataFlow

## Quickstart Guide

The easiest way to install SciDataFlow on Unix-like operating systems (e.g.
MacOS, Linux, etc.) is to use the easy install script. This script first
detects if you have Rust on your system, and if not installs it. Then it will
install SciDataFlow via Rust's incredible `cargo` system. To run the easy
install script:

    $ https://raw.githubusercontent.com/vsbuffalo/scidataflow/main/easy_install.sh | bash

Then, test that the installation worked by running `sdf --help` in your
terminal. If you'd like to validate the checksums for the `easy_install.sh`
script first, see [Validating the Easy Install
Checksums](#validating-the-easy-install-checksums).

## Manual Installation 

Alternatively, you can do each step manually of the `easy_install.sh` system.
If you do not have Rust installed, you'll need to install it with Rustup. If
you're using Linux, MacOS, or other Unix-like operating system, run the
following in your terminal (for Windows or more details, see the [Rust
website](https://www.rust-lang.org/learn/get-started)):

```
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Once you have Rust installed on your system (e.g. if `cargo --version` works),
you can install SciDataFlow in your terminal with:

```
$ cargo install scidataflow
```

## Validating the Easy Install Checksums

If you are security-conscious, you can check the MD5 of SHA1 digests as below:

    $ curl https://raw.githubusercontent.com/vsbuffalo/scidataflow/main/easy_install.sh | md5
    75d205a92b63f30047c88ff7e3de1a9f

    $ curl https://raw.githubusercontent.com/vsbuffalo/scidataflow/main/easy_install.sh | sha256sum
    0a654048b932a237cb93a9359900919188312867c3b7aeea23843272bc616a71  -
