---
layout: post
title: Set the Default Git Diff Tool on Windows
---

By default, Git is configured to use `vimdiff` at the command line. This can be set to a friendlier tool with a few configuration changes. Use `git difftool --tool-help` to show a list of the available tools. To configure Git to use [KDiff3](http://kdiff3.sourceforge.net/), for example, the only prerequisite is that it is installed.

The default diff tool can be configured with a few short commands:

```
git config --global diff.tool kdiff3
git config --global difftool.kdiff3.path "C:\Program Files\KDiff3\kdiff3.exe"
git config --global difftool.kdiff3.trustExitCode false
```

All diffs will now be opened with KDiff3 when using `git difftool`. To prevent Git from prompting before opening each file, use `git difftool -y` as described in the [docs](https://git-scm.com/docs/git-difftool).

To configure a separate GUI diff tool, use:

```
git config --global diff.guitool kdiff3
```

This can be used with `git difftool --gui -y`.
