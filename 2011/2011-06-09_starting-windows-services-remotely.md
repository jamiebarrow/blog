# 2011-06-09 Starting Windows Services Remotely

tags: cmd, command prompt, sc, services, tips, Windows

Did you know you can use the [sc command](https://docs.microsoft.com/en-us/windows/win32/services/controlling-a-service-using-sc) to start services remotely?

```shell
sc \\SERVERNAME start SERVICENAME
```

e.g.

```shell
sc \\test-server query AppFabricCachingService
sc \\test-server start AppFabricCachingService
```
