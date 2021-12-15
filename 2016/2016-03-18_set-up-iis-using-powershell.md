# 2016-03-18 Set up IIS using PowerShell

tags: IIS, powershell, Windows Server

When you're setting up a new server there are sometimes steps you need to do before you can configure your website, such as turning on Windows Authentication in corporate environments, or perhaps installing the features necessary for an ASP.NET application.

Usually this is done via the Server Manager, however this can be automated via PowerShell using something similar to the below (I formatted this on separate lines for readability, you will want to run it as a single line):


```powershell
Get-WindowsFeature -Name Web-*
    | Where-Object
    {
      ($_.Name -eq "Web-Asp-Net45" -or $_.Name -eq "Web-Windows-Auth")
      -and
      $_.InstallState -ne "Installed"
    }
    | Install-WindowsFeature
```

There are also more advanced options to the cmdlets, more information of which can be seen in [the documentation](https://docs.microsoft.com/en-us/powershell/module/servermanager/install-windowsfeature).

