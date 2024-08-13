# Setting Persistent Environment Variable in PowerShell

tags: powershell, terminal, windows

Today I learned that it is possible to set an environment variable that will stay persistent in the machines configuration on Windows.

For example, if I wanted to add `c:\flutter\bin` to the `PATH`, I can do the below from an Administrator prompt:

```powershell
[Environment]::SetEnvironmentVariable("PATH", $Env:PATH + ";c:\flutter\bin", [EnvironmentVariableTarget]::Machine)
```

Actually, there is a small error with the above, since it uses the `PATH` from the current process, and actually a better form would be:

```powershell
[Environment]::SetEnvironmentVariable("PATH", [Environment]::GetEnvironmentVariable("PATH", "Machine") + ";c:\flutter\bin", [EnvironmentVariableTarget]::Machine)
```

The value of `[System.EnvironmentVariableTarget]::Machine` is just the string `"Machine"` so this is also equivalent to the below, which may be easier to type:

```powershell
[Environment]::SetEnvironmentVariable("PATH", [Environment]::GetEnvironmentVariable("PATH", "Machine") + ";c:\flutter\bin", "Machine")
```

Make sure its from an Adminstrator PowerShell prompt. If the user doesn't have permission, you'll see the below error message:

```shell
Exception calling "SetEnvironmentVariable" with "3" argument(s): "Requested registry access is not allowed."
At line:1 char:1
+ [Environment]::SetEnvironmentVariable("PATH", $Env:PATH + ";c:\flutte ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], MethodInvocationException
    + FullyQualifiedErrorId : SecurityException
```

Finally, also be aware that it updates only the Machine scope, and does not add this to the environment of the current process.

## References:

- PowerShell docs [about_Environment_Variables](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.2#saving-environment-variables-with-setenvironmentvariable)
