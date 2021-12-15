# 2012-02-01 Symbolic links and hard links in Windows

tags: cmd, command line, hard link, junction, junction point, mklink, symbolic link, tips, Windows, Windows 2000, Windows 2007, Windows XP

A lot of people coming from the Linux world would probably have at some point used [symbolic links](https://en.wikipedia.org/wiki/Symbolic_link) or soft links, and [hard links](https://en.wikipedia.org/wiki/Hard_link).

Windows has had shortcuts for a long time, but these are actually files that are used to point to other files, they aren't actually entries in the filesystem that merely reference other files, which is what the links are, meaning that shortcuts take up more space.

A lesser known fact about Windows is that it actually also has symbolic links, hard links, and also with Windows NTFS has the concept of a [junction point](https://en.wikipedia.org/wiki/NTFS_junction_point), which is a hard link for a directory. The differences between them is discussed quite nicely in the post ["Windows File Junctions, Symbolic Links and Hard Links"](https://ipggi.wordpress.com/2009/09/07/windows-file-junctions-symbolic-links-and-hard-links/).

It also appears that the capability has been around for a while, going back to Windows 2000. With Windows 7 and probably most newer Windows versions these days, there's also a nice command line tool `mklink` to help with this.

Open up a command line, type `mklink /?` and then try it out for yourself in a test area, playing with creating new files, linking to them, deleting the original files, seeing how the links are affected, etc.

<strong>Disclaimer:</strong> If you delete something that wasn't just a pointer to a file, and was the actual file, that's your own fault, don't come looking for me :D
