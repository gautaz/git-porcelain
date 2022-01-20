# [git] [porcelain](http://stackoverflow.com/a/6976506)

Additional porcelain for [git]:

- git-lconfig
- git-rename-branch
- git-scores

## git-lconfig

The main idea behind this tool is to apply as easily as possible custom configurations to [git] repositories and in particular [multiple user configurations](https://orrsella.com/2013/08/10/git-using-different-user-emails-for-different-repositories/).

:warning: In order to avoid committing with the wrong user (TL;DR of the previous link):

```sh
# Require setting user.name and email per-repo:
$ git config --global user.useConfigOnly true

# Remove email address from global config:
$ git config --global --unset-all user.email
```

That said, `lconfig` takes predefined configuration sets from the file `~/.gitlconfig` and apply them to [git] repositories.

Type `git lconfig -h` in order to get help about the tool's usage and `git lconfig --help-ini` to get help about the `~/.gitlconfig` file format which basically comes down to:

```ini
[profile name 1]
git_var1 = value1
git_var2 = value2

[profile name 2]
git_var3 = value3
```

This tool depends on:

- [bash]
- [cat]
- [git]
- [GNU awk]
- [sed]

## git-rename-branch

Simple porcelain to quickly rename a branch locally **and** remotely.

The syntax is quite simple (see `git rename-branch -h`).

## git-scores

This tool will gather log information in the current repository in order to summarize contributions.

No command line help is available for now, the only option is to change the default sorting column which is currently the one detailing the number of changes made by a contributor.
Passing the 1-based column number to sort with will change this default behavior (i.e.: `git scores 3`).

A typical output is:

```
   Commits    Changes        (+)        (-)      Delta                                   Author
        40       5099       2973       2126        847                            XXXXXXXXXXXXX
         1        757        415        342         73                                 YYYYYYYY
        46        642        322        320          2                          ZZZZZZZZZZZZZZZ
```

This tool depends on:

- [bash]
- [git]
- [iconv]
- [sort]
- [tput]

[git]: https://git-scm.com/
[bash]: https://www.gnu.org/software/bash/
[cat]: http://pubs.opengroup.org/onlinepubs/9699919799/utilities/cat.html
[sed]: http://pubs.opengroup.org/onlinepubs/9699919799/utilities/sed.html
[GNU awk]: https://www.gnu.org/software/gawk/
[tput]: http://pubs.opengroup.org/onlinepubs/9699919799/utilities/tput.html
[iconv]: http://pubs.opengroup.org/onlinepubs/9699919799/utilities/iconv.html
[sort]: http://pubs.opengroup.org/onlinepubs/9699919799/utilities/sort.html
