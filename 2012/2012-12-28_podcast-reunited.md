# 2012-12-28 Podcast Reunited

tags: id3, iTunes, Podcast, PODCASTCATEGORY, PODCASTDESC, PODCASTID, PODCASTURL

I used to struggle to get iTunes to download podcasts properly. Sometimes they wouldn't download fully, or couldn't be resumed and had to be re-started (IIRC, might have just been other downloads that did this). So I would download them as MP3's from the shows' archive websites, e.g. with [.NET Rocks!](https://www.dotnetrocks.com/).

There is a problem with this though. When you add the files to iTunes, they are picked up as normal music, and not podcasts. This is sorted out easily by going into the file info and changing the Media Type to Podcast. Simple.

What is not so simple is why there are now two separate podcast entries - one for the subscription we used before, and one for the episodes that were downloaded manually. I used to ignore this, and just have them all on one playlist, but recently when I was re-importing everything into iTunes on a re-installed PC, I noticed this again and wanted to solve the issue.

MP3 files come tagged with ID3 tags. The standard ones such as artist, album, track number, etc. are easily edited in most audio programs, including iTunes. But for podcasts, there are some extended ones, namely PODCAST, PODCASTURL, PODCASTID, etc., which I found out using a program called Mp3tag.

You can update these tags using [Mp3tag](https://www.mp3tag.de/en/), and probably other software. For more info on this, [see the question I asked (and answered) on Superuser](https://superuser.com/q/525028/69108).

