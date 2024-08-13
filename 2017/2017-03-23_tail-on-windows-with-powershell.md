# 2017-03-23 tail on Windows with PowerShell

tags: command line, powershell, tips

One of the well known Unix/Linux commands is `tail`, which gets the tail of a file, meaning the end of a file and prints it out to the output stream.

I used to try find nice programs for this, including [Baretail](https://www.baremetalsoft.com/baretail/) which has some very nice features like colouring lines in that match certain patterns etc.

But if you just want a simple, and now built into Windows solution, just use PowerShell:


```powershell
Get-Content -Tail 10 filename.txt
```

This will show the last 10 lines of the file. You can even follow the tail, or watch it for changes, as below:


```powershell
gc -Tail 10 -Wait filename.txt
```

Another nice thing you can do is then pipe this into `Select-String` to filter the output:


```powershell
gc -Tail 10 -Wait filename.txt | Select-String -Pattern somepattern
```
