gitl
====

`gitl` is a collection of command-line git/github scripts.


Examples
--------

Get a quick list of recent unpushed commits in the current branch:

    $ git l
    dac6cc8 Fix git-bc <BRANCH> LOCAL
    8b0e105 Document git-bc -m option
    4681a29 Fix missing newline
    4e47ab8 Make git out independent of GITHUB_REPOS setting
    8b46445 cleanup

Create a pull request for the current branch:

    $ git pull-request
    # (opens your browser)

Get an overview of all outgoing branches:

    $ git out
    master
    2a6261b Clarify

    new-feature (not in upstream)
    a8ffaa0 Add mysterious new feature

Move the last commit into a separate feature branch and 
file a pull request for it:

    $ git move-cherry -b my-new-feature HEAD
    $ git pull-request my-new-feature
    # (opens your browser)

Open a page about the current repository, file, or revision in your browser:

    $ git info -w
    $ git info -w README.md
    $ git info -w HEAD

Configuration
-------------

Just put these scripts on your PATH.

If you want, you can use these scripts to customize your prompt.
Just run `gitl-setup -p` to get a prompt that shows the current
git branch and/or tag. 

To use `git-list-pull-requests`, the `gitl-setup` command can create a
github API key and show a list of settings to add to the `.profile`
file in your home directory (only required for `git-list-pull-requests`).

Command Reference
-----------------

### git-l

Quick log of the current branch, compared to origin/master.

### git-pull-request

Submit a GitHub pull request of the current or specified branch. Checks if it is still up-to-date using `git-is-current`, then opens your browser.

Arguments:

* `-f`       Don't fetch
* `-o`       Open the page for an existing pull request
* `BRANCH`   Request branch BRANCH

### git-out

Show an overview of all outgoing branches. Branches starting with `_` are not fully shown. 

Arguments:

* `-f`       Don't fetch
* `BRANCH`   Only show branch BRANCH
* `head`     Only show the current branch

### git-list-pull-requests

List all your open pull requests and shows if they are up-to-date 
compared to master (using `git-is-current)`.

Arguments:

* `-f`             Don't fetch
* `-q`             Be quiet
* `-w`             Open a web page instead

### git-is-current

Determine if the current or specified branch is up-to-date compared to the current branch,
or if merging the two branches would cause a conflict.

Arguments:

* `-f`             Don't fetch
* `-q`             Be quiet
* `origin/BRANCH`  Compare to branch origin/BRANCH instead of origin/master
* `BRANCH`         Use selected branch

### git-push-branch

Push the current branch or a given branch. Accepts the same arguments as git push,
e.g. supports git-push-branch --force, or git-push-branch --force branch2 to push
branch2 to origin.

### git-get-branch

Show the current branch.

### git-add-cherry

Extends or creates a branch with a cherry picking range of commits or local changes.

Usage: `git-add-cherry [-f] [-b] [<origin/BRANCH>] <BRANCH> [<CHERRY..> | LOCAL]`

* `-f`              disable fetch step
* `-b`              create a new branch BRANCH, rather than use an existing one
* `-p`              make a pull request for the new branch
* `origin/BRANCH`   name for base branch
* `BRANCH`          name for new branch
* `CHERRY`          a commit, a branch to pick the head from, or a range of commits [default: HEAD]
* `LOCAL`           take uncommited changes instead of a range of commits

### git-move-cherry

Extends or creates a branch with a cherry picking range of commits or local changes,
moving them away from the current branch.

Usage: `git-move-cherry [-f] [-b] [<origin/BRANCH>] <BRANCH> [<CHERRY..> | LOCAL]`

* `-f`              disable fetch step
* `-b`              create a new branch BRANCH, rather than use an existing one
* `-p`              make a pull request for the new branch
* `origin/BRANCH`   name for base branch
* `BRANCH`          name for new branch
* `CHERRY`          a commit, a branch to pick the head from, or a range of commits [default: HEAD]
* `LOCAL`           take uncommited changes instead of a range of commits

### git-keep-alive

Maintains an open connection to speed up github access. See http://coderrr.wordpress.com/2011/10/31/github-hack-speed-up-git-push-and-git-pull/.

### git-info

Show information about the current repository or a path within the repository.

Usage: `git-info [-w] [PATH | REVISION]`

* `-w`             Open a web page in your browser
* `PATH`           A path to show info for

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

