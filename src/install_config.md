# Welcome to SciDataFlow!

![SciDataFlow demo screencast](https://github.com/vsbuffalo/scidataflow/blob/6c7294f33498b9d77e4e0b830502b9c0719ed6db/screencast.gif)

**Problem 1**: Have you ever wanted to reuse and build upon a research
project's output or supplementary data, but can't find it?

**SciDataFlow** solves this issue by making it easy to **unite** a research
project's *data* with its *code*. Often, code for open computational projects
is managed with Git and stored on a site like GitHub. However, a lot of
scientific data is too large to be stored on these sites, and instead is hosted
by sites like  [Zenodo](http://zenodo.org) or [FigShare](http://figshare.com). 

**Problem 2**: Does your computational project have dozens or even hundreds of
intermediate data files you'd like to keep track of? Do you want to see if
these files are changed by updates to computational pipelines.

SciDataFlow also solves this issue by keeping a record of the necessary
information to track when data is changed. This is stored alongside the
information needed to retrieve data from and push data to remote data
repositories. All of this is kept in a simple [YAML](https://yaml.org) "Data
Manifest" (`data_manifest.yml`) file that SciDataFlow manages. This file is
stored in the main project directory and meant to be checked into Git, so that
Git commit history can be used to see changes to data. The Data Manifest is a
simple, minimal, human and machine readable specification. But you don't need
to know the specifics — the simple `sdf` command line tool handles it all for
you.

Before we get started with learning to use SciDataFlow, you'll need
to [install it](install.html), as well as [configure some very basic
user information](config.html) (don't worry — it's only one command!).
