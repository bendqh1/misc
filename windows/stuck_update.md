## 1

```powershell
Install-Module PSWindowsUpdate -Force
Import-Module PSWindowsUpdate
```

* If asked to install NuGet:<br>
NuGet is a Microsoft package manager required to download PowerShell modules like PSWindowsUpdate. It's safe and necessary in this context.

## 2

```powershell
Hide-WindowsUpdate -Title "UPDATE_TITLE_COMES_HERE_EXACTLY_AS_WRITTEN"
```

* If getting an error about the lack of ability to run scripts due to to Powershell execution policy.<br>
To proceed safely, temporarily allow scripts for your current session only:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

And only then:

```powershell
Hide-WindowsUpdate -Title "UPDATE_TITLE_COMES_HERE_EXACTLY_AS_WRITTEN"
```

## 3

Restart the PC and check for updates.
