# Installing SciDataFlow

## Quickstart Guide



## 

The easiest way to install SciDataFlow is to use the easy install script, which
detects if you have Rust on your system, and if not installs it. Then it will
install SciDataFlow via Rust's incredible `cargo` system. To run the easy
install script:

    $ https://raw.githubusercontent.com/vsbuffalo/scidataflow/main/easy_install.sh | bash

If you are security-conscious, you can check the MD5 of SHA1 digests as below:

    $ curl https://raw.githubusercontent.com/vsbuffalo/scidataflow/main/easy_install.sh | md5
    75d205a92b63f30047c88ff7e3de1a9f

    $ curl https://raw.githubusercontent.com/vsbuffalo/scidataflow/main/easy_install.sh | sha256sum
    0a654048b932a237cb93a9359900919188312867c3b7aeea23843272bc616a71  -

If you'd like to the Rust Programming Language manually, [see this
page](https://www.rust-lang.org/tools/install), which instructs you to run:

```
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Then, to install SciDataFlow, just run:

```console 
$ cargo install scidataflow
```

To test, just try running `sdf --help`.



