# Introduction to SciDataFlow

First, make sure you have [installed](chapter_2.html) and
[configured](chapter_3.html) SciDataFlow.

The user interacts with the Data Manifest through the fast and concurrent
command line tool `sdf` written in the inimitable [Rust
language](https://www.rust-lang.org). The `sdf` tool has a Git-like interface.

If you know Git, using it will be easy, e.g. to initialize SciDataFlow for a
project you'd use:

```console
$ sdf init
```

Registering a file in the manifest: 

```console
$ sdf add data/population_sizes.tsv
Added 1 file.
```

Checking to see if a file has changed, we'd use `sdf status`:

```console
$ sdf status
Project data status:
0 files on local and remotes (1 file only local, 0 files only remote), 1 file total.

[data]
 population_sizes.tsv      current      3fba1fc3      2023-09-01 10:38AM (53 seconds ago)
```

Now, let's imagine a pipeline runs and changes this file: 

```console
$ bash tools/computational_pipeline.sh # changes data
$ sdf status 
Project data status:
0 files on local and remotes (1 file only local, 0 files only remote), 1 file total.

[data]
 population_sizes.tsv      changed      3fba1fc3 → 8cb9d10b        2023-09-01 10:48AM (1 second ago)

```

If these changes are good, we can tell the Data Manifest it should update its
record of this version:

```console 
$ sdf update data/population_sizes.tsv
$ sdf status
Project data status:
0 files on local and remotes (1 file only local, 0 files only remote), 1 file total.

[data]
 population_sizes.tsv      current      8cb9d10b      2023-09-01 10:48AM (6 minutes ago)

```

**⚠️Warning**: SciDataFlow does not do data *versioning*. Unlike Git, it does
not keep an entire history of data at each commit. Thus, **data backup must be
managed by separate software**. SciDataFlow is still in alpha phase, so it is
especially important you backup your data *before* using SciDataFlow. A tiny,
kind reminder: you as a researcher should be doing routine backups *already* —
losing data due to either a computational mishap or hardware failure is always
possible. 


