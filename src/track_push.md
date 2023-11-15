# Tracking and Pushing Files to a Remote

## Tracking Files with `sdf track`

SciDataFlow knows you probably don't want to upload *every* file that
you're keeping track of locally. Sometimes you just want to use
SciDataFlow to track local changes. So, in addition to files being
registered in the Data Manifest, you can also tell them you'd like to
*track* them:

```console
$ sdf track data/population_sizes.tsv
```

Now, you can check the status on remotes too with:

```console
$ sdf status --remotes
Project data status:
1 file local and tracked by a remote (0 files only local, 0 files only remote), 1 file total.

[data > Zenodo]
 population_sizes.tsv      current, tracked      8cb9d10b      2023-09-01 10:48AM (14 minutes ago)      not on remote
```

## Uploading Files with `sdf push`

Then, to upload these files to Zenodo, all we'd do is:

```console
$ ../target/debug/sdf push
Info: uploading file "data/population_sizes.tsv" to Zenodo
Uploaded 1 file.
Skipped 0 files.
```
