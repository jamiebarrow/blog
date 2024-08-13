# 2017-07-20 git - exclude files in a diff

tags: git, node_modules

In some scenarios you might have a build server that doesn't have access to the Internet, in which case if you're working with something like npm, you might need to commit your node_modules folder to the git repository to get stuff to work.

Of course, it might be better to setup your own artifact repository such as Nexus on an internal network for these dependencies, BUT, I didn't have that! :D The node_modules are included as part of a commit.

Having to do a code review of a pull request can be tricky because of this, due to more than 10,000 files being in the commit, of which only 40 are actual source files of interest. We're using TFS 2017 which has a nice web interface for doing this, however it only supports showing 1000 files at a time.

So back to the best way to use git: the command line :)

To exclude the node_modules from the diff was as simple as doing the below:


```shell
$ git diff master develop -- . ':!node_modules'
```

Of course, I used `difftool` because I prefer WinMerge but it works the same.

