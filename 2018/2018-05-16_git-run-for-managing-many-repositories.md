# 2018-05-16 git-run for managing many repositories

tags: bash, git, tips

Some may make use of a monorepo, [for example over there at Google](https://cacm.acm.org/magazines/2016/7/204032-why-google-stores-billions-of-lines-of-code-in-a-single-repository/fulltext), however for those of us that don't and have to deal with multiple repositories, possibly unrelated ones across various projects, then a great tool to have in your toolbelt is [git-run](https://github.com/mixu/gr), or just `gr`.

It can keep track of where your repositories are located, and can also be used to tag the various repositories. You can then run a git command across all of these repositories (or based on a tag).

To set it up:


```shell
$ npm install -g git-run
$ git tag discover PATH
```

One way I have been using that is to create a tag per project, so across a project which may have many repositories, I can see my git status across all of those by executing:


```shell
$ gr @project status
```

It can also run normal shell commands as well:


```shell
$ gr @project cat package.json
```

One thing I realised it didn't do in my git bash shell, was run my aliases that I tend to use (e.g. I have a complicated bash alias for a git log command). But luckily someone else has already got an open [pull request](https://github.com/mixu/gr/pull/27/files) to fix this (at least for bash), which suited my needs. Yay for open source!

Try it out and let me know what you think :)

<b>Update:</b> I also recently discovered when trying it on a new computer - make sure you don't forget to add tags to the repositories it discovers during `gr tag discover`, because it won't save its configuration and [you'll get an error](https://github.com/mixu/gr/issues/88).

