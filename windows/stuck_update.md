In Powershell:

```powershell
Install-Module PSWindowsUpdate -Force
Import-Module PSWindowsUpdate
```

You may be asked to install NuGet.<br>
NuGet is a Microsoft package manager required to download PowerShell modules like PSWindowsUpdate. It's safe and necessary in this context.

You may get an error about the lack of ability to run scripts due to to Powershell execution policy.<br>
To proceed safely, temporarily allow scripts for your current session only:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Do the rest and then hide the update:

```
Hide-WindowsUpdate -Title "UPDATE_TITLE_COMES_HERE_EXACTLY_AS_WRITTEN"
```

Restart the PC and try to update.
