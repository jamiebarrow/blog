# 2013-02-14 Git tip - diff of only modified files

tags: git, tips

I was wondering how to see a diff of only those items that were modified in my Git workspace, and thanks to Stackoverflow, you can use the `--diff-filter` parameter:


```shell
$ git diff --diff-filter=M
$ git dt --diff-filter=M
```

The second one is if you use a visual diff tool. I prefer [WinMerge](https://winmerge.org/), might do a post on my setup at some point, it's pretty simple once you know how.

