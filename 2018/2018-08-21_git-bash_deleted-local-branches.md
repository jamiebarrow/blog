# 2018-08-21 git bash - deleted local branches

tags: bash, git, git branches, tips

You can find out which branches have been merged into a branch by running the below:

```shell
$ git branch --merged origin/master
* master
  feature/some-branch
  feature/some-other-branch
```

This will also print out master as part of it, so we can then pipe that into grep to match results without master:

```shell
$ git branch --merged origin/master | grep -v master
  feature/some-branch
  feature/some-other-branch
```

Obviously, you won't want the name `master` in your branch name, otherwise it'll be excluded too. You can fancier with regex here.

Now we can take this result and pipe it into xargs, to run git branch -d passing the output as arguments:

```shell
$ git branch --merged origin/master
  | grep -v master
  | xargs -r git branch -d
```

I'm splitting up the command onto separate lines for readability. The `-r` will only run the git command if there is output.

I've noticed this doesn't always delete all old branches, but it can help. For example, perhaps you had a branch that was a work in progress, or a spike, with changes that aren't merged - this won't be picked up.

You can do one more trick to detect old branches that have no upstream branch anymore:

```shell
$ git branch -vv
```

This will list branches without an upstream branch with `gone`. Those can generally be deleted too.
