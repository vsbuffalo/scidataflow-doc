# Retrieving Data from Static URLs

Often we also want to retrieve data from URLs. For example, many
genomic resources are available for download from the
[UCSC](http://genome.ucsc.edu) or [Ensembl](http://ensembl.org)
websites as static URLs. We want a record of where these files come
from in the Data Manifest, so we want to combine a download with a
`sdf add`. This is where `sdf get` and `sdf bulk` come in handy.

## Downloading Data from URLs: `sdf get`

The command `sdf get` does this all for you — let's
imagine you want to get all human coding sequences. You could do this with: 

```console
$ sdf get https://ftp.ensembl.org/pub/release-110/fasta/homo_sapiens/cds/Homo_sapiens.GRCh38.cds.all.fa.gz
⠄ [================>                       ] 9639693/22716351 (42%) eta 00:00:08
```

Now, it would show up in the Data Manifest:

```console
$ sdf status --remotes
Project data status:
0 files local and tracked by a remote (0 files only local, 0 files only remote), 1 files total.

[data > Zenodo]
 Homo_sapiens.GRCh38.cds.all.fa.gz      current, untracked      fb59b3ad      2023-09-01  3:13PM (43 seconds ago)      not on remote
```

Note that files downloaded from URLs are not automatically track with remotes.
You can do this with `sdf track <FILENAME>` if you want. Then, you can use `sdf
push` to upload this same file to Zenodo or FigShare. 


## Bulk Downloading Data with `sdf get`

Since modern computational projects may require downloading potentially
*hundreds* or even *thousands* of annotation files, the `sdf` tool has a simple
way to do this: tab-delimited or comma-separated value files (e.g. those with
suffices `.tsv` and `.csv`, respectively). The big picture idea of SciDataFlow
is that it should take mere seconds to pull in all data needed for a large
genomics project (or astronomy, or ecology, whatever). Here's an example TSV
file full of links:

```console
$ cat human_annotation.tsv
type	url
cdna	https://ftp.ensembl.org/pub/release-110/fasta/homo_sapiens/cdna/Homo_sapiens.GRCh38.cdna.all.fa.gz
fasta	https://ftp.ensembl.org/pub/release-110/fasta/homo_sapiens/dna/Homo_sapiens.GRCh38.dna.alt.fa.gz
cds	https://ftp.ensembl.org/pub/release-110/fasta/homo_sapiens/cds/Homo_sapiens.GRCh38.cds.all.fa.gz
```

Note that this has a header, and the URLs are in the second column. To get this data, we'd use: 

```console
$ sdf bulk human_annotation.tsv --column 2 --header
⠁ [                                        ] 0/2 (0%) eta 00:00:00
⠉ [====>                                   ] 9071693/78889691 (11%) eta 00:01:22
⠐ [=========>                              ] 13503693/54514783 (25%) eta 00:00:35
```

**Columns indices are one-indexed** and `sdf bulk` assumes no headers by
default. Note that in this example, only two files are downloading — this is
because `sdf` detected the CDS file already existed. SciDataFlow tells you this
with a little message at the end: 

```console 
$ sdf bulk human_annotation.tsv --column 1 --header
3 URLs found in 'human_annotation.tsv.'
2 files were downloaded, 2 added to manifest (0 were already registered).
1 files were skipped because they existed (and --overwrite was no specified).
```

Note that one can also download files from URLs that are in the Data Manifest.
Suppose that you clone a repository that has no remotes, but each file entry
has a URL set. Those can be retrieved with:

```console
$ sdf pull --urls  # if you want to overwrite any local files, use --ovewrite
```

These may or may not be `tracked`; tracking only indicates whether to *also*
manage them with a remote like Zenodo or FigShare. In cases where the data file
can be reliable retrieved from a steady source (e.g. a website like the UCSC
Genome Browser or Ensembl) you may not want to duplicate it by also tracking
it. If you want to pull in *everything*, use:

```console
$ sdf pull --all
```


