# Packit dev

## Prerequisites

First, install the deploy tool

```
pip3 install --user packit-deploy
```

Ensure that the path that the script is copied into is in your path (on Linux, most likely `~/.local/bin`, on OSX `~/Library/Python/<version>/bin`

Clone this repo

```
git clone https://github.com/reside-ic/packit-dev
```

All other commands are exectuted from within `packit-dev/`

## Initial bootstrap

Set up an initial volume with enough for the server to start up with. This will get easier once `outpack_server` knows how to do this.

```
docker volume remove packit_outpack_volume
docker volume create packit_outpack_volume
docker run --rm -v packit_outpack_volume:/packit -w /packit \
  mrcide/orderly2:mrc-4514 \
  bash -c "git clone https://github.com/mrc-ide/malaria-sites-orderly . \
    && R -e 'orderly2::orderly_init(\".\", use_file_store = TRUE, path_archive = NULL, require_complete_tree = TRUE)'"
```

## Start

```
packit start config
```

## Upgrading

It is possible that the `packit-deploy` deploy scripts should be updated

```
pip3 install --user --upgrade packit-deploy
```

Then redeploy with:

```
packit stop config
packit start --pull config
```
