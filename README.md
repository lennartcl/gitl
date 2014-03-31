gitl
====

`gitl` is a collection of command-line git & github scripts.
Most of these scripts operate fully in the command-line, but some
of them can interact with github/bitbucket to open a pull request, or
display some information about an item in the repository.

Examples
--------

Get a quick list of recent non-master commits in the current branch:

    $ git l
    dac6cc8 Fix git-bc <BRANCH> LOCAL
    8b0e105 Document git-bc -m option
    4681a29 Fix missing newline
    4e47ab8 Make git out independent of GITHUB_REPOS setting
    8b46445 cleanup

Create a pull request for the current branch:

    $ git pull-request
    # (opens your browser with github.com or bitbucket.org)

Open a web page about the current repository, file, or revision in your browser:

    $ git info -w
    $ git info -w README.md
    $ git info -w HEAD

Get an overview of all outgoing branches:

    $ git out --all
    master
    2a6261b Something directly committed to master :o

    feature-x
    8a8ffa1 Done. Going to bed now.
    644abff WIP

    feature-y
    a8ffaa0 Add mysterious new feature

Move the last commit into a separate feature branch and 
file a pull request for it:

    $ git cherry-move -b my-new-feature HEAD
    $ git pull-request my-new-feature
    # (opens your browser)

Installation
------------

Just put these scripts on your PATH and they'll work.
Instead of invoking a script directly, like `git-info`,
you can also type `git info`.

If you like, you can get a fancy prompt with some extra
info about the current branch using `git prompt`.

Command Reference
-----------------

### git-l

Usage: `git l [BRANCH]`

Quick log of the current or given branch, compared to origin/master.

### git-cherry-copy

Extends or creates a branch with a cherry picking range of commits or local changes.

Usage: `git cherry-copy [-f] [-b] [<origin/BRANCH>] <BRANCH> <CHERRY.. | LOCAL>`

* `-f`              disable fetch step
* `-b`              create a new branch BRANCH, rather than use an existing one
* `-p`              make a pull request for the new branch
* `origin/BRANCH`   name for base branch
* `BRANCH`          name for new branch
* `CHERRY`          a commit, a branch to pick the head from, or a range of commits [default: HEAD]
* `LOCAL`           take uncommited changes instead of a range of commits

### git-cherry-move

Extends or creates a branch with a cherry picking range of commits or local changes,
moving them away from the current branch.

Usage: `git cherry-move [-f] [-b] [<origin/BRANCH>] <BRANCH> <CHERRY.. | LOCAL>`

* `-f`              disable fetch step
* `-b`              create a new branch BRANCH, rather than use an existing one
* `-p`              make a pull request for the new branch
* `origin/BRANCH`   name for base branch
* `BRANCH`          name for new branch
* `CHERRY`          a commit, a branch to pick the head from, or a range of commits [default: HEAD]
* `LOCAL`           take uncommited changes instead of a range of commits

### git-info

Show information about the current repository or a path within the repository.

Usage: `git info [-w] [PATH | REVISION]`

* `-w`             Open a web page in your browser
* `PATH`           A path to show info for

### git-is-current

Determine if the current or specified branch is up-to-date compared to the current branch,
or if merging the two branches would cause a conflict.

Arguments:

* `-f`             Don't fetch before comparison
* `-q`             Be quiet
* `origin/BRANCH`  Compare to branch origin/BRANCH instead of origin/master
* `BRANCH`         Use selected branch

### git-out

Show an overview of all outgoing branches. Branches starting with `_` are not fully shown. 

Arguments:

* `-a|--all`  Show all branches
* `-f`        Don't fetch
* `BRANCH`    Only show branch BRANCH

### git-pull-request

Submit a GitHub pull request of the current or specified branch. Checks if it is
still up-to-date using `git-is-current`, then opens your browser.

Arguments:

* `-f`       Don't fetch before doing a pull request (faster, can't guarantee it won't conflict)
* `-o`       Open the page for an existing pull request
* `BRANCH`   Request branch BRANCH

License (MIT)
-------------

Permission is hereby granted, free of charge, to any person obtaining a copy of this
software and associated documentation files (the "Software"), to deal in the Software
without restriction, including without limitation the rights to use, copy, modify,
merge, publish, distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be included in all copies
or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A
PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

