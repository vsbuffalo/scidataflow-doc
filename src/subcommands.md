# All `sdf` subcommands

Below is a list of all SciDataFlow subcommands for the `sdf` tool.
This list can also be access anytime (along with some examples of
commonly used `sdf` subcommands) with `sdf --help`).


**Main Subcommands** 

- `sdf config`: Set local system-wide metadata (e.g., your name, email, etc.), which can be propagated to some APIs. See [Configuring SciDataFlow](config.html).
- `sdf init`: Initialize a new project. See [Initializing a Project with sdf init and sdf metadata](init.html).
- `sdf metadata`: Change the project metadata. See [Setting Project Metadata](init.html#setting-project-metadata)
- `sdf add`: Add a data file to the manifest. See [Adding files with `sdf add`](add.html#adding-files-with-sdf-add).
- `sdf status`: Show status of data. See [Checking for file modifications with `sdf status`](add.html#checking-for-file-modifications-with-sdf-status).
- `sdf update`: Update MD5s. See [Checking for file modifications with `sdf status`](add.html#adding-a-modified-version-of-data-to-the-data-manifest).
- `sdf rm`: Remove a file from the manifest. See [Adding/Removing Files and Getting File Status with `sdf add`, `sdf rm`, and `sdf status`](add.html#removing-a-file-from-the-manifest-with-sdf-rm)
- `sdf mv`: Move or rename a file on the file system and in the manifest. See [Moving a File with `sdf mv`](add.html#moving-a-file-with-sdf-mv)

**Remote Subcommands** 

- `sdf link`: Link a directory to a remote storage solution. See [Linking to a Remote with sdf link](link.html#linking-to-a-remote-with-sdf-link)
- `sdf get`: Download a file from a URL. See [Downloading Data from Static URLs](get_bulk.html#downloading-data-from-urls-sdf-get)
- `sdf bulk`: Download a bunch of files from links stored in a file. See [Bulk Downloading Data with `sdf bulk`](get_bulk.html#bulk-downloading-data-with-sdf-get)
- `sdf track`: Start tracking a file on the remote. See [Tracking Files with `sdf track`](track_push.html#tracking-files-with-sdf-track)
- `sdf untrack`: Stop tracking a file on the remote. See [Untracking a File with `sdf untrack`](track_push.html#untracking-a-file).
- `sdf pull`: Pull in all tracked files from the remote. See [Retrieving Data from Remotes](pull.html).
- `sdf push`: Push all tracked files to remote. See [Pushing Files to Remotes](track_push.html#uploading-files-with-sdf-push).
- `sdf asset`: Retrieve a SciDataFlow Asset. See [SciDataFlow Assets](assets.html).
- `sdf help`: Print all subcommands with examples, or the help for a specific subcommand.

