# 2017-11-30 bash startup files and aliases

tags: bash, command line, git, linux

Today I hosted a Beer and Tech session at Entelect on [Automating Database Deployments (with Flyway)](/blog/2015-12-02/getting-started-with-automating-database-changes-using-flyway).

During the session, I was using the Bash terminal to edit files or run Flyway, and interacting with git quite a bit - as we all know, using git on the command line is the best way to do so ;D

After the session, a colleague asked me how I created shortcuts for certain commands, and I explained to him how Bash supports aliases and that these can be loaded by a startup file. There are [various startup files](https://www.gnu.org/software/bash/manual/bash.html#Bash-Startup-Files-1), but I tend to use ~/.bash_profile and not ~/.bashrc. Here are some of the shortcuts I currently have setup:


```shell
alias cls='clear'
alias l='ls -Al'
alias ..='cd ..'

alias gf='git fetch --prune'
alias gl='git log --name-status --abbrev-commit'
alias grh='git reset --hard'
alias gs='git status'
```

And so on. If you modify the file, you have to re-load these into the current session, or restart a new terminal session. To reload the file, you can just do the following:


```shell
$ . ~/.bash_profile
```

Hope this helped someone :)

