# 2017-03-20 diff PDF files

tags: diff, ghostscript, imagemagick, pdf, png

At a client we have a PDF template that needs to be used for registering users. When this is updated, the template is overriden. But it would be nice to be able to easily see what changed between the two.

Well, this is possible :)

You can use [ImageMagick](https://imagemagick.org/) and [Ghostscript](https://ghostscript.com/) to do this.

You should be able to just do the below:


```shell
magick compare old.pdf new.pdf diff.pdf
```
But that didn't seem to work well. What seems to work better is to rather convert the PDF to an image first, and then compare each page.


```shell
magick convert -density 300 -quality 100 old.pdf old.png
magick convert -density 300 -quality 100 new.pdf new.png

magick compare old-0.png new-0.png diff-0.png
```

Depending on the options you can get better or worse results. Changing the colorspace to CMYK for example could yield better results, or maybe using options to blur/sharpen/despeckle the image too. Try play around with the options to see better results.

The best results I had was actually via using Adobe Acrobat to first export the PDF to images, and then run the compare. I still need to figure out why, because unfortunately I only have the license at work, so this won't always be an option.

