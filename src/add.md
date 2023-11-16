# Adding/Removing Files and Getting File Status with `sdf add`, `sdf rm`, and `sdf status`

## Adding files with sdf add

To add a file to the `data_manifest.yml`, we use `sdf add`:

```console
$ sdf add data/population_sizes.tsv
Added 1 file.
```

This will add an entry into the `files` section in the
`data_manifest.yml` with this file, including its MD5 hash.

## Checking for file modifications with sdf status

To check if a file has changed, use `sdf status`. Let's look at the
status of the file we just added with `sdf add`:

```console
$ sdf status
Project data status:
0 files on local and remotes (1 file only local, 0 files only remote), 1 file total.

[data]
 population_sizes.tsv      current      3fba1fc3      2023-09-01 10:38AM (53 seconds ago)
```

Since this file has not been modified since its creation, its status
is **current**.

Now, let's imagine a pipeline runs and changes this file: 

```console
$ bash tools/computational_pipeline.sh # changes data
$ sdf status 
Project data status:
0 files on local and remotes (1 file only local, 0 files only remote), 1 file total.

[data]
 population_sizes.tsv      changed      3fba1fc3 → 8cb9d10b        2023-09-01 10:48AM (1 second ago)

```

Now, the status indicates that this file has been **changed**.

## Adding a Modified Version of Data to the Data Manifest with `sdf update`

If these changes are good, we can tell the Data Manifest it should
update its record of this version:

```console 
$ sdf update data/population_sizes.tsv
$ sdf status
Project data status:
0 files on local and remotes (1 file only local, 0 files only remote), 1 file total.

[data]
 population_sizes.tsv      current      8cb9d10b      2023-09-01 10:48AM (6 minutes ago)

```

## Removing a File from the Manifest with `sdf rm`

One can remove a data file entry from the Data Manifest with `sdf
rm`. **Note that this does not remove the file**; you can do this
separately with the Unix `rm` command.

```console
$ sdf rm data/population_sizes.tsv
```

## Moving a File with `sdf mv`

Much like the Git subcommand `git mv`, `sdf` has `sdf mv` subcommand
that can be used to move a file's location in the manifest and on
the file system:


```console
$ sdf mv data/population_sizes.tsv old_data/population_sizes.tsv
```


