#GitCommands



Translated Versions

A list of my commonly used Git commands

Getting & Creating Projects

Command	Description</br>
git init	Initialize a local Git repository</br>
git clone ssh://git@github.com/[username]/[repository-name].git	Create a local copy of a remote repository</br>

Basic Snapshotting
Command	Description

git status	Check status</br>
git add [file-name.txt]	Add a file to the staging area</br>
git add -A	Add all new and changed files to the staging area</br>
git commit -m "[commit message]"	Commit changes</br>
git rm -r [file-name.txt]	Remove a file (or folder)</br>

Branching & Merging
Command	Description

git branch	List branches (the asterisk denotes the current branch)</br>
git branch -a	List all branches (local and remote)</br>
git branch [branch name]	Create a new branch</br>
git branch -d [branch name]	Delete a branch</br>
git push origin --delete [branch name]	Delete a remote branch</br>
git checkout -b [branch name]	Create a new branch and switch to it</br>
git checkout -b [branch name] origin/[branch name]	Clone a remote branch and switch to it</br>
git branch -m [old branch name] [new branch name]	Rename a local branch</br>
git checkout [branch name]	Switch to a branch</br>
git checkout -	Switch to the branch last checked out</br>
git checkout -- [file-name.txt]	Discard changes to a file</br>
git merge [branch name]	Merge a branch into the active branch</br>
git merge [source branch] [target branch]	Merge a branch into a target branch</br>
git stash	Stash changes in a dirty working directory</br>
git stash clear	Remove all stashed entries</br>


Sharing & Updating Projects
Command	Description


git push origin [branch name]	Push a branch to your remote repository</br>
git push -u origin [branch name]	Push changes to remote repository (and remember the branch)</br>
git push	Push changes to remote repository (remembered branch)</br>
git push origin --delete [branch name]	Delete a remote branch</br>
git pull	Update local repository to the newest commit</br>
git pull origin [branch name]	Pull changes from remote repository</br>
git remote add origin ssh://git@github.com/[username]/[repository-name].git	Add a remote repository</br>
git remote set-url origin ssh://git@github.com/[username]/[repository-name].git	Set a repository's origin branch to SSH</br>
Inspection & Comparison
Command	Description
git log	View changes</br>
git log --summary	View changes (detailed)</br>
git log --oneline	View changes (briefly)</br>
git diff [source branch] [target branch]	Preview changes before merging</br>


==============================================================================================================================

Setup and Config</br>

===============================================================================================================================

-------------------------------------------------------------------------------------------------------------------------------

NAME</br>

-------------------------------------------------------------------------------------------------------------------------------

git - the stupid content tracker</br>

-------------------------------------------------------------------------------------------------------------------------------


SYNOPSIS</br>

-------------------------------------------------------------------------------------------------------------------------------
git [-v | --version] [-h | --help] [-C <path>] [-c <name>=<value>]
    [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
    [-p|--paginate|-P|--no-pager] [--no-replace-objects] [--bare]
    [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
    [--config-env=<name>=<envvar>] <command> [<args>]</br>


-------------------------------------------------------------------------------------------------------------------------------

DESCRIPTION</br>

-------------------------------------------------------------------------------------------------------------------------------


Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals.</br>

See gittutorial[7] to get started, then see giteveryday[7] for a useful minimum set of commands. The Git User’s Manual has a more in-depth introduction.</br>

After you mastered the basic concepts, you can come back to this page to learn what commands Git offers. You can learn more about individual Git commands with "git help command". gitcli[7] manual page gives you an overview of the command-line command syntax.</br>

A formatted and hyperlinked copy of the latest Git documentation can be viewed at https://git.github.io/htmldocs/git.html or https://git-scm.com/docs.</br>

-------------------------------------------------------------------------------------------------------------------------------

OPTIONS</br>

-------------------------------------------------------------------------------------------------------------------------------

-v</br>
--version</br>
Prints the Git suite version that the git program came from.</br>

This option is internally converted to git version ... and accepts the same options as the git-version[1] command. If --help is also given, it takes precedence over --version.</br>

-h</br>
--help</br>
Prints the synopsis and a list of the most commonly used commands. If the option --all or -a is given then all available commands are printed. If a Git command is named this option will bring up the manual page for that command.</br>

Other options are available to control how the manual page is displayed. See git-help[1] for more information, because git --help ... is converted internally into git help ....</br>

-C <path></br>
Run as if git was started in <path> instead of the current working directory. When multiple -C options are given, each subsequent non-absolute -C <path> is interpreted relative to the preceding -C <path>. If <path> is present but empty, e.g. -C "", then the current working directory is left unchanged.</br>

This option affects options that expect path name like --git-dir and --work-tree in that their interpretations of the path names would be made relative to the working directory caused by the -C option. For example the following invocations are equivalent:</br>

git --git-dir=a.git --work-tree=b -C c status</br>
git --git-dir=c/a.git --work-tree=c/b status</br>
-c <name>=<value></br>
Pass a configuration parameter to the command. The value given will override values from configuration files. The <name> is expected in the same format as listed by git config (subkeys separated by dots).</br>

Note that omitting the = in git -c foo.bar ... is allowed and sets foo.bar to the boolean true value (just like [foo]bar would in a config file). Including the equals but with an empty value (like git -c foo.bar= ...) sets foo.bar to the empty string which git config --type=bool will convert to false.</br>

--config-env=<name>=<envvar></br>
Like -c <name>=<value>, give configuration variable <name> a value, where <envvar> is the name of an environment variable from which to retrieve the value. Unlike -c there is no shortcut for directly setting the value to an empty string, instead the environment variable itself must be set to the empty string. It is an error if the <envvar> does not exist in the environment. <envvar> may not contain an equals sign to avoid ambiguity with <name> containing one.</br>

This is useful for cases where you want to pass transitory configuration options to git, but are doing so on OS’s where other processes might be able to read your cmdline (e.g. /proc/self/cmdline), but not your environ (e.g. /proc/self/environ). That behavior is the default on Linux, but may not be on your system.</br>

Note that this might add security for variables such as http.extraHeader where the sensitive information is part of the value, but not e.g. url.<base>.insteadOf where the sensitive information can be part of the key.</br>

--exec-path[=<path>]</br>
Path to wherever your core Git programs are installed. This can also be controlled by setting the GIT_EXEC_PATH environment variable. If no path is given, git will print the current setting and then exit.</br>

--html-path</br>
Print the path, without trailing slash, where Git’s HTML documentation is installed and exit.</br>

--man-path</br>
Print the manpath (see man(1)) for the man pages for this version of Git and exit.</br>

--info-path</br>
Print the path where the Info files documenting this version of Git are installed and exit.</br>

-p</br>
--paginate</br>
Pipe all output into less (or if set, $PAGER) if standard output is a terminal. This overrides the pager.<cmd> configuration options (see the "Configuration Mechanism" section below).</br>

-P</br>
--no-pager</br>
Do not pipe Git output into a pager.</br>

--git-dir=<path></br>
Set the path to the repository (".git" directory). This can also be controlled by setting the GIT_DIR environment variable. It can be an absolute path or relative path to current working directory.</br>

Specifying the location of the ".git" directory using this option (or GIT_DIR environment variable) turns off the repository discovery that tries to find a directory with ".git" subdirectory (which is how the repository and the top-level of the working tree are discovered), and tells Git that you are at the top level of the working tree. If you are not at the top-level directory of the working tree, you should tell Git where the top-level of the working tree is, with the --work-tree=<path> option (or GIT_WORK_TREE environment variable)</br>

If you just want to run git as if it was started in <path> then use git -C <path>.</br>

--work-tree=<path></br>
Set the path to the working tree. It can be an absolute path or a path relative to the current working directory. This can also be controlled by setting the GIT_WORK_TREE environment variable and the core.worktree configuration variable (see core.worktree in git-config[1] for a more detailed discussion).</br>

--namespace=<path></br>
Set the Git namespace. See gitnamespaces[7] for more details. Equivalent to setting the GIT_NAMESPACE environment variable.</br>

--bare</br>
Treat the repository as a bare repository. If GIT_DIR environment is not set, it is set to the current working directory.</br>

--no-replace-objects</br>
Do not use replacement refs to replace Git objects. See git-replace[1] for more information.</br>

--literal-pathspecs</br>
Treat pathspecs literally (i.e. no globbing, no pathspec magic). This is equivalent to setting the GIT_LITERAL_PATHSPECS environment variable to 1.</br>

--glob-pathspecs</br>
Add "glob" magic to all pathspec. This is equivalent to setting the GIT_GLOB_PATHSPECS environment variable to 1. Disabling globbing on individual pathspecs can be done using pathspec magic ":(literal)"</br>

--noglob-pathspecs</br>
Add "literal" magic to all pathspec. This is equivalent to setting the GIT_NOGLOB_PATHSPECS environment variable to 1. Enabling globbing on individual pathspecs can be done using pathspec magic ":(glob)"</br>

--icase-pathspecs</br>
Add "icase" magic to all pathspec. This is equivalent to setting the GIT_ICASE_PATHSPECS environment variable to 1.</br>

--no-optional-locks</br>
Do not perform optional operations that require locks. This is equivalent to setting the GIT_OPTIONAL_LOCKS to 0.</br>

--list-cmds=group[,group…​]</br>
List commands by group. This is an internal/experimental option and may change or be removed in the future. Supported groups are: builtins, parseopt (builtin commands that use parse-options), main (all commands in libexec directory), others (all other commands in $PATH that have git- prefix), list-<category> (see categories in command-list.txt), nohelpers (exclude helper commands), alias and config (retrieve command list from config variable completion.commands)</br>

--attr-source=<tree-ish></br>
Read gitattributes from <tree-ish> instead of the worktree. See gitattributes[5]. This is equivalent to setting the GIT_ATTR_SOURCE environment variable.</br>

GIT COMMANDS</br>

We divide Git into high level ("porcelain") commands and low level ("plumbing") commands.</br>


High-level commands (porcelain)</br>
We separate the porcelain commands into the main commands and some ancillary user utilities.</br>

Main porcelain commands</br>

git-add[1]</br>
Add file contents to the index</br>

git-am[1]</br>
Apply a series of patches from a mailbox</br>

git-archive[1]</br>
Create an archive of files from a named tree</br>

git-bisect[1]</br>
Use binary search to find the commit that introduced a bug</br>

git-branch[1]</br>
List, create, or delete branches</br>

git-bundle[1]</br>
Move objects and refs by archive</br>

git-checkout[1]</br>
Switch branches or restore working tree files</br>

git-cherry-pick[1]</br>
Apply the changes introduced by some existing commits</br>

git-citool[1]</br>
Graphical alternative to git-commit</br>

git-clean[1]</br>
Remove untracked files from the working tree</br>

git-clone[1]</br>
Clone a repository into a new directory</br>

git-commit[1]</br>
Record changes to the repository</br>

git-describe[1]</br>
Give an object a human readable name based on an available ref</br>

git-diff[1]</br>
Show changes between commits, commit and working tree, etc</br>

git-fetch[1]</br>
Download objects and refs from another repository</br>

git-format-patch[1]</br>
Prepare patches for e-mail submission</br>

git-gc[1]</br>
Cleanup unnecessary files and optimize the local repository</br>

git-grep[1]</br>
Print lines matching a pattern</br>

git-gui[1]</br>
A portable graphical interface to Git</br>

git-init[1]</br>
Create an empty Git repository or reinitialize an existing one</br>

git-log[1]</br>
Show commit logs</br>

git-maintenance[1]</br>
Run tasks to optimize Git repository data</br>

git-merge[1]</br>
Join two or more development histories together</br>

git-mv[1]</br>
Move or rename a file, a directory, or a symlink</br>

git-notes[1]</br>
Add or inspect object notes</br>

git-pull[1]</br>
Fetch from and integrate with another repository or a local branch</br>

git-push[1]</br>
Update remote refs along with associated objects</br>

git-range-diff[1]</br>
Compare two commit ranges (e.g. two versions of a branch)</br>

git-rebase[1]</br>
Reapply commits on top of another base tip</br>

git-reset[1]</br>
Reset current HEAD to the specified state</br>

git-restore[1]</br>
Restore working tree files</br>

git-revert[1]</br>
Revert some existing commits</br>

git-rm[1]</br>
Remove files from the working tree and from the index</br>

git-shortlog[1]</br>
Summarize git log output</br>

git-show[1]</br>
Show various types of objects</br>

git-sparse-checkout[1]</br>
Reduce your working tree to a subset of tracked files</br>

git-stash[1]</br>
Stash the changes in a dirty working directory away</br>

git-status[1]</br>
Show the working tree status</br>

git-submodule[1]</br>
Initialize, update or inspect submodules</br>

git-switch[1]</br>
Switch branches</br>

git-tag[1]</br>
Create, list, delete or verify a tag object signed with GPG</br>

git-worktree[1]</br>
Manage multiple working trees</br>

gitk[1]</br>
The Git repository browser</br>

scalar[1]</br>
A tool for managing large Git repositories</br>

Ancillary Commands</br>
Manipulators:</br>

git-config[1]</br>
Get and set repository or global options</br>

git-fast-export[1]</br>
Git data exporter</br>

git-fast-import[1]</br>
Backend for fast Git data importers</br>

git-filter-branch[1]</br>
Rewrite branches</br>

git-mergetool[1]</br>
Run merge conflict resolution tools to resolve merge conflicts</br>

git-pack-refs[1]</br>
Pack heads and tags for efficient repository access</br>

git-prune[1]</br>
Prune all unreachable objects from the object database</br>

git-reflog[1]</br>
Manage reflog information</br>

git-remote[1]</br>
Manage set of tracked repositories</br>

git-repack[1]</br>
Pack unpacked objects in a repository</br>

git-replace[1]</br>
Create, list, delete refs to replace objects</br>

Interrogators:</br>

git-annotate[1]</br>
Annotate file lines with commit information</br>

git-blame[1]</br>
Show what revision and author last modified each line of a file</br>

git-bugreport[1]</br>
Collect information for user to file a bug report</br>

git-count-objects[1]</br>
Count unpacked number of objects and their disk consumption</br>

git-diagnose[1]</br>
Generate a zip archive of diagnostic information</br>

git-difftool[1]</br>
Show changes using common diff tools</br>

git-fsck[1]</br>
Verifies the connectivity and validity of the objects in the database</br>

git-help[1]</br>
Display help information about Git</br>

git-instaweb[1]</br>
Instantly browse your working repository in gitweb</br>

git-merge-tree[1]</br>
Perform merge without touching index or working tree</br>

git-rerere[1]</br>
Reuse recorded resolution of conflicted merges</br>

git-show-branch[1]</br>
Show branches and their commits</br>

git-verify-commit[1]</br>
Check the GPG signature of commits</br>

git-verify-tag[1]</br>
Check the GPG signature of tags</br>

git-version[1]</br>
Display version information about Git</br>

git-whatchanged[1]</br>
Show logs with difference each commit introduces</br>

gitweb[1]</br>
Git web interface (web frontend to Git repositories)</br>

Interacting with Others</br>
These commands are to interact with foreign SCM and with other people via patch over e-mail.</br>

git-archimport[1]</br>
Import a GNU Arch repository into Git</br>

git-cvsexportcommit[1]</br>
Export a single commit to a CVS checkout</br>

git-cvsimport[1]</br>
Salvage your data out of another SCM people love to hate</br>

git-cvsserver[1]</br>
A CVS server emulator for Git</br>

git-imap-send[1]</br>
Send a collection of patches from stdin to an IMAP folder</br>

git-p4[1]</br>
Import from and submit to Perforce repositories</br>

git-quiltimport[1]</br>
Applies a quilt patchset onto the current branch</br>

git-request-pull[1]</br>
Generates a summary of pending changes</br>

git-send-email[1]</br>
Send a collection of patches as emails</br>

git-svn[1]</br>
Bidirectional operation between a Subversion repository and Git</br>

