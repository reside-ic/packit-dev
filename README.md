# Packit dev

## Prerequisites

First, install the deploy tool

```
pip3 install --user packit-deploy
```

Ensure that the path that the script is copied into is in your path (on Linux, most likely `~/.local/bin`, on OSX `~/Library/Python/<version>/bin`

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
