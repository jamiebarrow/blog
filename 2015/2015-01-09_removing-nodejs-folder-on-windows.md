# 2015-01-09 Removing NodeJS folder on Windows

tags: nodejs, Windows

When playing around with demo projects on NodeJS, and then later trying to throw them away and delete the folders, you've most likely encountered the error: <b>The file name is too long</b>. We'll ignore the question of if it's too long, how it got created in the first place...

To illustrate it, create a folder that will cause a long file path. I've had this problem with `grunt-contrib-imagemin`, so lets install that package too:


```shell
cd \tmp
mkdir this-is-probably-a-really-long-folder-name
cd this-is-probably-a-really-long-folder-name
mkdir yeah-it-probably-is
cd yeah-it-probably-is
npm init
npm install grunt-contrib-imagemin -D
```

Now, if you try and delete this folder, you will get the pesky <b>The file name is too long</b> error:


```shell
cd \tmp
rmdir /s /q this-is-probably-a-really-long-folder-name
this-is-probably-a-really-long-folder-name\YEAH-I~1\NODE_M~1\GRUNT-~1\NODE_M~1\imagemin\NODE_M~1\IMF332~1\NODE_M~1\gifsicle\NODE_M~1\BIN-BU~1\NODE_M~1\download\NODE_M~1\DECOMP~2\NODE_M~1\TAR-ST~1\NODE_M~1\END-OF~1\NODE_M~1\once\NODE_M~1\wrappy\package.json - The file name is too long.
...
```

Le sigh.

If you manually try and change into that directory, at some point you'll also get an issue where you can't even change into it because the filename is too long. But wait, if you look at the above, everything is using short file names except the first folder. Hmm, what if we try the short file name?


```shell
dir /x
rmdir /s /q THIS-I~1
```

It works! Well, it did for me at least.

