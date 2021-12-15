# 2013-02-07 Easier way to get to that hosts file

tags: cmd, command line, command prompt, junction, junction point, mklink

In Windows, there's a hosts file mapping IP addresses to hostnames. For some weird reason, it's in the arbitrary location of `c:\windows\system32\drivers\etc\hosts`. This kinda reminds me of a Unix/Linux path, with the `\etc\hosts`. But anyway. That's often too much to type in when just trying to go `Start -> Run -> notepad++ hosts`. So, use symbolic links :) Something else that is Unix/Linux like, that not many people know exist on Windows:


```shell
C:\> mklink hosts c:\windows\system32\drivers\etc\hosts
symbolic link created for hosts <<===>> c:\windows\system32\drivers\etc\hosts
```

Then you can just say `notepad++ \hosts`.

Much easier.

