# Configuring SciDataFlow

Much like Git, the SciDataFlow command line tool has a user configuration file
stored in the user's home directory (at `~/.scidataflow_config`). Currently,
this configuration file is predominantly used to store user metadata, such as
full name, email, affiliation. Since some remote data repositories like Zenodo
require this information, SciDataFlow automatically propagates this metadata
from the configuration file.

You can set your user metadata with:

```console
$ sdf config --name "Joan B. Scientist" \
      --email "joanbscientist@berkeley.edu" \
      --affiliation "UC Berkeley"
```

In the future, other user-specific configurations will be stored here too.
