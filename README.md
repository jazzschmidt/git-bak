# git-bak
Fully backups and archives a Git repository in a tar ball. The backup archive is equipped with a convenient clone script.

## Overview
Output from `--help` argument:
````lang=shell
$ ./git-bak --help
NAME
    git-bak - Backup a Git repository

SYNOPSIS
    git-bak [-x] [-f archive] -u url

DESCRIPTION
    Backups a Git repository by bundling it with all its references. The bundle is then packed as tar ball.
    The archive will be placed in the current directory by default.

    Unless otherwise specified via '-x' or '--no-script', a simple script to conveniently clone the bundle into
    the current directory is added to archive.

OPTIONS:
    -f, --file <FILE>   Custom path for the generated tar ball
    -u, --url <URL>     Tells which url to clone the Git repository from
    -h, --help          Shows this help message
    -v, --verbose       Increases verbosity
    -x, --no-script     Skips creation of the clone script

EXAMPLES:
    Backup a remote repository that is saved as 'repo.tar.gz' in the current directory along with the clone script.

        git-bak -u https://example.com/projects/repo.git
````

## Example Usage

Create the Backup
````lang=shell
$ ./git-bak -u https://github.com/jazzschmidt/git-bak.git -f archive.tar.gz
````

Unpack the archive
````lang=shell
$ tar -xzf archive.tar.gz
$ ls -loh
total 112
-rw-r--r--  1 user    23K Apr 16 17:16 archive.tar.gz
-rwxr-xr-x  1 user   163B Apr 16 17:16 checkout
-rw-r--r--  1 user    24K Apr 16 17:16 gitbundle
````

Clone the repo
````lang=shell
$ ./checkout
Cloning into 'git-bak'...
Receiving objects: 100% (190/190), 23.97 KiB | 7.99 MiB/s, done.
Resolving deltas: 100% (77/77), done.
````
