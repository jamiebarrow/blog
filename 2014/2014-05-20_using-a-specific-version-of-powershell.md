# 2014-05-20 Using a specific version of PowerShell

tags: powershell

If you inspect `$PSVersionTable` you'll see a few different versions of things being used with PowerShell in the current session, specifically look for `$PSVersionTable.PSVersion`. By default the most latest version will be used.

To launch a specific version of PowerShell you can pass the `-version` switch, e.g. for PowerShell v2:


```shell
C:\> powershell -version 2
```
