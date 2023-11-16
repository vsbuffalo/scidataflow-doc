# Retrieving Data from Remotes

A key feature of SciDataFlow is that it can quickly reunite a project's *code*
repository with its *data*. Imagine a colleague had a small repository
containing the code lift a recombination map over to a new reference genome,
and you'd like to use her methods. However, you also want to check that you can
reproduce her pipeline on your system, which first involves re-downloading all
the input data (in this case, the original recombination map and liftover
files).

First, you'd clone the repository: 

```console
$ git clone git@github.com:mclintock/maize_liftover
$ cd maize_liftover/
```

Then, as long as a `data_manifest.yml` exists in the root project directory
(`maize_liftover/` in this example), SciDataFlow is initialized. You can verify
this by using:

```console
$ sdf status  --remotes
Project data status:
1 file local and tracked by a remote (0 files only local, 0 files only remote), 1 file total.

[data > Zenodo]
 recmap_genome_v1.tsv      deleted, tracked      7ef1d10a            exists on remote
 recmap_genome_v2.tsv      deleted, tracked      e894e742            exists on remote
```

Now, to retrieve these files, all you'd need to do is: 

```console
$ sdf pull 
Downloaded 1 file.
 - population_sizes.tsv
Skipped 0 files. Reasons:
```

Note that if you run `sdf pull` again, it will not redownload the file (this is
to over overwriting the local version, should it have been changed): 

```console
$ sdf pull
No files downloaded.
Skipped 1 files. Reasons:
  Remote file is indentical to local file: 1 file
   - population_sizes.tsv
```

If the file has changed, you can pull in the remote's version with `sdf pull
--overwrite`. However, `sdf pull` is also lazy; it will not download the file
if the MD5s haven't changed between the remote and local versions. 

Downloads with SciDataFlow are fast and concurrent thanks to the [Tokio Rust
Asynchronous Universal download MAnager](https://github.com/rgreinho/trauma)
crate. If your project has a lot of data across multiple remotes, SciDataFlow
will pull all data in as quickly as possible. 

