# SciDataFlow Assets

Good scientific workflows should create shareable **Scientific Assets** that
are *trivial* to download and build upon in your own scientific work.
SciDataFlow makes this possible, since in essence each `data_manifest.yml` file
is like a minimal recipe specification for also how to *retrieve* data.  The
`sdf asset` command simply downloads a `data_manifest.yml` from
SciDataFlow-Assets, another GitHub repository, or URL. After this is
downloaded, all files can be retrieved in one line:

    $ sdf asset nygc_gatk_1000G_highcov
    $ sdf pull --all

The idea of SciDataFlow-Assets is to have a open, user-curated
collection of these recipes at
[https://github.com/scidataflow-assets](https://github.com/scidataflow-assets).
Considering contributing an Asset when you release new data with a
paper!

