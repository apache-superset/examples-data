# Superset Examples Repository

This repo holds/serves the examples for the Apache Superset ecosystem that are accessed by the `superset examples` command.

## Listing Examples

Examples can be listed via the Apache Superset CLI:

`superset examples list —-help`

```bash
Usage: superset examples list [OPTIONS]

  List example Slices/Dashboards/datasets

Options:
  -r, --examples-revision TEXT  Revision of examples to list
  --help                        Show this message and exit.
```

## Contributing Examples

This repository can be used to submit Apache Superset examples. Install the system requirements below, and then follow 
the contributing instructions.

### System Requirements

In order to contribute examples you will need Git LFS to contribute the data that goes along with your Dashboard export 
`dashboard.json` file.

Creating, removing, listing and loading examples can be handled without Git LFS but adding examples to this directory of 
examples will require it. 

Git LFS can be [installed](https://github.com/git-lfs/git-lfs/wiki/Installation) via:

```bash
# OS X
brew install git-lfs
# port install git-lfs
git lfs install
```

```bash
# Ubuntu
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
sudo apt-get install git-lfs
git lfs install
```

## Contributing an Example

To export an example dashboard from Apache Superset, use the `superset examples create` command to produce a gzipped 
tarball. 

`superset examples create --help`

```bash
Usage: superset examples create [OPTIONS]

  Create example Slice/Dashboard/datasets

Options:
  -i, --dashboard-id INTEGER  Specify dashboard id to export
  -t, --dashboard-title TEXT  Specify dashboard title to export
  -d, --description TEXT      Description of new example  [required]
  -e, --example-title TEXT    Title for new example  [required]
  -f, --file-name TEXT        Specify export file name. Defaults to
                              dashboard.tar.gz
  -l, --license TEXT          License of the example dashboard
  --help                      Show this message and exit.
```

For example, to export the `World's Bank Data` example, you would run the following:

```bash
superset examples create \
    --dashboard-title "World's Bank Data" \
    --description "World Bank Data on global population trends from 1960 through 2010" \
    --example-title "World Bank Data" \
    --file-name "world_bank_example.tar.gz" \
    --license "Apache 2.0"
```

Next, copy and then expand the tarball into the root directory of this project. Git add the directory this creates, commit 
and push the changes to your own branch and then submit a pull request to 
[https://github.com/apache/examples-data](https://github.com/apache/examples-data). Once approved, your example will 
automatically be listed among the available examples listed by the `superset examples list` command.
