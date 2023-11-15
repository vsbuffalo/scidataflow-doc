# Linking to a remote with sdf link

Once you have your personal authentication tokens, you can link a
subdirectory to a remote using `sdf link`:

```console
$ sdf link  data/ zenodo <TOKEN> --name popsize_study
```

You only need to link a remote once. SciDataFlow will look for a
project on the remote with this name first (see `sdf link --help` for
more options). SciDataFlow stores the authentication keys for all
remotes in `~/.scidataflow_authkeys.yml` so you don't have to
remember them. This file can be manually edited, e.g. if your
personal access token changes.

