# Initializing a Project with `sdf init` and `sdf metadata`

To initialize SciDataFlow for a project you'd use:

```console
$ sdf init
```

This creates an empty `data_manifest.yml` file (much like Git creates
the `.git/` directory):

```console
$ ls -l
total 8
-rw-r--r--@ 1 vsb  staff  66 Nov 15 15:20 data_manifest.yml

$ cat data_manifest.yml
files: []
remotes: {}
metadata:
  title: null
  description: null
```

This empty `data_manifest.yml` file will be edited by the various
`sdf` subcommands.

## Setting Project Metadata

Projects can also have store metadata, such as a title and
description. This is kept in the Data Manifest. You can set this
manually with: 

```console
$ sdf metadata --title "genomics_analysis" --description "A re-analysis of Joan's data."
```

