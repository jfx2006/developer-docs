---
description: >- Use the new bootstrap script to automatically setup
your development repository!
---

# Bootstrapping a development repository

This document will help get a development repository set up on your
own computer. Even on a fast connection, this can take ten to fifteen minutes of
work, spread out over an hour or two.

## Requirements

### Linux

* A 64-bit Linux distribution 
* Python 2.7 **and** Python 3.6 or higher

### Windows

* 64-bit Windows
* Visual Studio 2017
* The MozillaBuild package
* See [Windows Build Prerequisites](windows-build-prerequisites.md)

### macOS

* Xcode Command Line Tools
* macOS SDK 10.12 or higher
* See [macOS Build Prerequisites](macos-build-prerequisites.md)

## Bootstrap a copy of the source code

### Download the script

Download the [bootstrap script](https://hg.mozilla.org/comm-central/raw-file/default/python/rocboot/bin/bootstrap.py)
using whatever method is easiest for you. Save it anywhere you like, just
be able to find it using a shell. (eg. MozillaBuild's msys on Windows.)

```shell
curl -O bootstrap.py https://hg.mozilla.org/comm-central/raw-file/default/python/rocboot/bin/bootstrap.py 
```

### Run the script

The bootstrap script runs with Python 3.

```shell
python3 bootstrap.py
```

{% hint style="info" %}
The bootstrap script defaults to using Mercurial. However, if you’d prefer to use
`git`, you can grab the source code in “git” form by running the bootstrap script
with the `vcs` parameter:

```shell
python3 bootstrap.py --vcs=git
```

This uses [Git Cinnabar](https://github.com/glandium/git-cinnabar/) under the hood.

### Artifact builds

Artifact builds are discussed [here](artifact-builds.md). If you are not modifying
C/C++/Rust code, they are a real time saver.

To set up the environment to use artifact builds, use `--artifact-mode`.

```shell
python3 bootstrap.py --artifact-mode
```

### Enter checkout path

The script will prompt for a location to create the repository. It doesn't have
to be a complete path, if you enter just a directory name it will checkout into
the current directory.

### qaStaH nuq jay’?

This takes a while ...

### Qapla'!

Navigate to your checkout directory.

A `mozconfig` file will be present set up for building Thunderbird in full-build
or artifact mode.

```shell
./mach build
./mach run
```

# 🎉 wo’ batlhvaD!

## Optimize your build

The `mozconfig` file is the bare minimum needed. Making your build go faster will
save you hours of frustration! It's highly recommended that you review the rest
of build documentation to fine-tune your setup. 

## Bugs? Help?

This script is new for Thunderbird 91, and likely has problems. You can talk to
`:rjl` in Matrix for help. Maybe `:darktrojan` 😉. 
