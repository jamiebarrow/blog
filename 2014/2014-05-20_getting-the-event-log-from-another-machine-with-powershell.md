# 2014-05-20 Getting the Event Log from another machine with PowerShell

tags: powershell

If you have to manage a server farm of more than one computer, PowerShell can be of use if you have access to it.

If you don't have access to it, you may have to setup PowerShell Remoting (don't ask me how, because I haven't done that myself yet).


```shell
PS C:\> Get-EventLog -ComputerName somecomputer -LogName Application -Newest 10
```

Note that I'm using the `-Newest` paramter and not using the `-After` parameter, because apparently this means you will need to wait for PowerShell to go through the entire log, instead of stopping at a certain point.

