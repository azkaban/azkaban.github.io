---
layout: default
nav: contributing
title: "How to Contribute"
---

<p class="lead">We always welcome contributions to help make Azkaban better. Please take a moment to 
read this document if you would like to contribute. Please feel free to reach out on the 
<a href="https://groups.google.com/forum/?fromgroups#!forum/azkaban-dev" target="_blank">Azkaban Google Group</a> 
if you have any questions.</p>

### Reporting issues

We use [Github issues](https://github.com/azkaban/azkaban/issues) to track bug reports, feature requests, 
and submitting pull requests.

If you find a bug:

 1. Use the GitHub issue search to check whether the bug has already been reported.
 2. If the issue has been fixed, try to reproduce the issue using the latest `master` branch of the repository.
 3. If the issue still reproduces or has not yet been reported, try to isolate the problem before opening an issue.

### Pull requests

We welcome bug fixes, improvements, and new features. Before embarking on making significant changes, 
please open an issue and ask first so that you do not risk duplicating efforts or spending time working 
on something that may be out of scope.

1. [Fork the project](https://help.github.com/fork-a-repo), clone your fork, and add the upstream to your remote:

    ```bash
    $ git clone git@github.com:<your-username>/azkaban.git
    $ cd azkaban
    $ git remote add upstream https://github.com/azkaban/azkaban.git
    ```

2. If you need to pull new changes committed upstream:

    ```bash
    $ git checkout master
    $ git fetch upstream
    $ git merge upstream/master
    ```
3. Create a feature branch for your fix or new feature:

    ```bash
    $ git checkout -b <feature-branch-name>
    ```

4. Please try to commit your changes in logical chunks and reference the issue number in your commit messages:

    ```bash
    $ git commit -m "Issue #<issue-number> - <commit-message>"
    ```

5. Push your feature branch to your fork.

    ```bash
    $ git push origin <feature-branch-name>
    ```

6. [Open a Pull Request](https://help.github.com/articles/using-pull-requests/) against the upstream `master` branch. 
Please give your pull request a clear title and description and note which issue(s) your pull request fixes.

**Important**: By submitting a patch, you agree to allow the project owners to license your work under the 
[Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0).  Additional information about contributing 
to the Azkaban project can be found [here](https://github.com/azkaban/azkaban/blob/master/CONTRIBUTING.md)
