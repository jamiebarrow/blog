# 2017-01-25 Uninstall Windows Service using PowerShell

tags: powershell, Windows

You can get a list of services using the `Get-Service` cmdlet, for example, to retrieve a list of all running services you could run:


```powershell
Get-Service | Where-Object { $_.Status -eq "Running" }
```

You could even retrieve a specific service and start/stop it:


```powershell
$service = Get-Service DemoService
$service.Start()
$service.Stop()
```

However, there is nothing to remove the service on this object.

We can also use `GetWmiObject` to do the same things:


```powershell
$service = Get-WmiObject Win32_Service -Filter "name='DemoService'"
$service.StartService()
$service.StopService()
```

But this WMI object actually also exposes a delete functionality, which will mark the service to be deleted.


```powershell
$service = Get-WmiObject Win32_Service -Filter "name='DemoService'"
$service.Delete()
```

If there are resources that are being held onto, it will only be deleted once they're freed up - whether it's the service that needs to gracefully shutdown still, or maybe the services manager snap-in (services.msc) has an open properties window open (closing the window then puts the delete through).

