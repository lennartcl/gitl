gitl
====

`gitl` is a collection of command-line git/github scripts.

Configuration
-------------

Just put these scripts on your PATH.

If you want, you can use these scripts to customize your prompt.
Just run `gitl-setup -p` to get a prompt that shows the current
git branch and/or tag. 

To use `git-list-pull-requests`, the `gitl-setup` command can create a
github API key and show a list of settings to add to the `.profile`
file in your home directory (only required for `git-list-pull-requests`).

Commands
--------

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

Determine if the current or specified branch is up-to-date compared to the current branch.

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

### git-branch-from-cherry, git-bc

Creates a new branch by cherry-picking a range of commits, or by copying current local changes to a new branch.

Usage: `git-branch-from-cherry [-f] [-b] [<origin/BRANCH>] <BRANCH> [<CHERRY..> | LOCAL]`

* `-f`              disable fetch step
* `-b`              create a new branch BRANCH, rather than use an existing one
* `-p`              make a pull request for the new branch
* `-m`              move the commit(s), instead of copying it
* `origin/BRANCH`   name for base branch
* `BRANCH`          name for new branch
* `CHERRY`          a commit, a branch to pick the head from, or a range of commits [default: HEAD]
* `LOCAL`           take uncommited changes instead of a range of commits

### git-keep-alive

Maintains an open connection to speed up github access. See http://coderrr.wordpress.com/2011/10/31/github-hack-speed-up-git-push-and-git-pull/.

### git-info

Show information about the current repository or a path within the repository.

Usage: `git-info [-w] [PATH]`

* `-w`             Open a web page
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

