# Exercise 1 - Examining your repository

In this exercise, you will explore a few different techniques for examining a git repository and it's history, including git log, git diff, and git show. You will first clone the repository containing this git course, and then examine it using the various tools. The sections covering git log and git diff are adapted from the following Atlassian tutorials:

https://www.atlassian.com/git/tutorials/git-log

https://www.atlassian.com/git/tutorials/saving-changes/git-diff

These tutorials offer a more comprehensive overview of the useful functionality of git log and git diff than presented here, so keep them in mind as a future reference.

* [Clone the git repository](#initialization)

* [Use git log](#log)

* [Use git diff](#diff)

* [Use git show](#show)

## Clone the git repository <a name="initialization"></a>

```plaintext
git clone git@github.com:C2SM/git-course
```

Navigate into the repository.

```plaintext
cd git-course
```

## Use git log to have a look at the repository <a name="log"></a>

The `git log` command lists the commits in the repository. You can use the various options for git log to format how the commits are displayed and/or filter which commits are displayed. Start with the basic command to see the default behavior. You can exit out of the log at any time by hitting the `q` key.

```plaintext
git log
```

Let's look at some of the ways that we can change how the commits are displayed.

To get a high-level overview of the repository, try the `--oneline` option:

```plaintext
git log --oneline
```

To get a brief summary of the changes introduced by each commit, use the `--stat` option:

```plaintext
git log --stat
```

To quickly see who has been working on what commits, use the `shortlog` command:

```plaintext
git shortlog
```

To get a picture of the history of the branch structure of the repository, use the `--graph` option. This option is particularly helpful when used in combination with the `--oneline` option.

```plaintext
git log --graph --oneline
```

Now, let's look at some of the ways we can filter commits using the `git log` options.  

To limit the number of commits displayed, try the `-` option:

```plaintext
git log -3
```

To see commits made by a certain author, use the `--author` option. This option accepts a regular expression and returns all commits whose author matches that pattern.  

```plaintext
git log --author="Jonas"
```

To see all the commits that changed one specific file, for example the `helpers.sh` file, try the following:

```plaintext
git log helpers.sh
```

To see all commits that introduce or remove a specific line of text, for example `Have fun!`, try the following:

```plaintext
git log -S 'Have fun!'
```

Remember that you can combine any of these git log options together to achieve your desired output. And if you decide on a format that you would like to use frequently, you can create an alias for this format using `git config`. For example, to set up an alias to use git log with the `--oneline` and `--graph` options, use the following command:

```plaintext
git config --global alias.lg "log --oneline --graph"
```

Now, if you use `git lg`, you will see the log with the options you specified. Note that you can create aliases for any git command using `git config` and this is a very powerful tool.


## Use git diff <a name="diff"></a>
The `git diff` command shows the differences between two different git data sources. These data sources can be commits, files, branches, tags and more. The `git diff` command can be used from the command line, but it can be difficult to interpret the output in that format. Therefore people often use a third-party visualization tool to examine the output of git diff. In this section, you will start by using `git diff` from the command line and then you will explore some of the options available for improving the readability of the output.

### git diff on the command line

To get started, let's make a new branch with a change in it.  

```plaintext
git switch -c difftest
```

Open the README.md file and make a change in it.

The default behavior of `git diff` is to show any uncommited changes since the last commit. Try this now.

```plaintext
git diff
```

Now, let's add and commit the change you made. Remember to make a meaningful commit message. Note that the `-a` option to the `git commit` command allows us to add any changed files to the staging area without having to separately use the `git add` command.

```plaintext
git commit -am "Put your commit message here"
```

You can use `git diff` to compare the content between branches, for example the main branch and the difftest branch:

```plaintext
git diff main difftest
```

You can also output the difference between one specific file in two different branches.

```plaintext
git diff main difftest ./README.md
```

Now let's use git diff to compare the difference between two commits. Use git log to get two commit IDs, and then put the two commit IDs as arguments to git diff.

```plaintext
git log
```

```plaintext
git diff 8eb59b37 f435db79
```

Here you can see that the output of git diff in the command line can be difficult to read if there are many changes. Let's have a look at some ways to better visualize these differences.

### git diff visualization options

#### git difftool

One way that you can better visualize the output of `git diff` is to use `git difftool`. This command is a wrapper for `git diff` that allows you to specify the diff tool of your choice to view the output in. You can see all of the possible tools with the `--tool-help` option.

```plaintext
git difftool --tool-help
```

Here you can see listed the available tools that are already installed on the system you are using, as well as the other tools that would work but you don't yet have installed.

Choose one of the installed tools on your system, and try `git difftool`. Use the `-t` option to specify which tool you want to use. For example, to use vimdiff, try:

```plaintext
git difftool -t vimdiff 8eb59b37 f435db79
```

This command allows you to step through all the files that were changed between the two commits one at a time and get a clearer picture of how the files were changed.  

#### Git web interface

Git web interfaces, such as Github and Gitlab, also have built in wrappers which help to visualize the output for `git diff`.

Let's have a look at the git course repository on Github. You can find it here:
https://github.com/C2SM/git-course

You can get to the `git diff` wrapper by adding `/compare` to any Github repository url. So have a look at:
https://github.com/C2SM/git-course/compare

This will open up a comparison interface in your web browser. Here you can use the gui provided to compare the code between branches and forks. You can also specify exact comparisons by changing the url. For example, to compare the same two commits we have compared with `git diff` and `git difftool`, you can use the following url:

https://github.com/C2SM/git-course/compare/8eb59b37..f435db79

You can find more information about how to use the Github compare tool [here](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/viewing-and-comparing-commits/comparing-commits).

Note: You may have noticed that the comparison we have done includes some binary (.png) files. Because these are binary files, you cannot get an exact difference between them, but the fact that they showed up in the `git diff` output means that the files have changed between the two commits. This can sometimes be useful information. Remember that it's best practice to try to avoid committing binary files into git repositories when possible. If it is necessary, try to keep the size of the files as small as possible to make it quick and easy to work with your git repository.

## Use git show <a name="show"></a>

The `git show` command is another command that can be used to examine git objects such as tags and commits. This command can be useful for examining commits because it shows not only the commit SHA and commit message like `git log` but additionally the difference in the files committed like `git diff`.  

Go back to your terminal window with the git course repository and try out the `git show` command.

```plaintext
git show
```

By default, this command shows us the latest commit, or HEAD in git terminology. You can see the commit SHA and message as well as the difference between any files that were changed in this commit. You could examine any commit in the repository by giving the commit SHA as an input to the `git show` command.

```plaintext
git show f435db79
```

Like `git log`, `git show` can be used with various options that allow you to change the way the information is displayed. There are options that change the way the commit SHA and message are displayed, such as `git show --oneline`. There are also options that change the way that the diff is displayed, but none of them really alleviate the problem that big diffs are generally hard to read in the terminal window. As with all git commands, you can use the `-h` option to get a description of all the possible options that can be used with `git show`.

```plaintext
git show -h
```
