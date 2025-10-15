## 1) Run Powershell as Administrator

```powershell
Install-Module PSWindowsUpdate -Force
Import-Module PSWindowsUpdate
```

* If asked to install NuGet:<br>
NuGet is a Microsoft package manager required to download PowerShell modules like PSWindowsUpdate. It's safe and necessary in this context.

## 2 Hide a given update

```powershell
Hide-WindowsUpdate -Title "UPDATE_TITLE_COMES_HERE_EXACTLY_AS_WRITTEN"
```

* If getting an error about the lack of ability to run scripts due to to Powershell execution policy.<br>
To proceed safely, temporarily allow scripts for your current session only:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

And only then run the command to hide the update.

## 3 Restart

Restart the PC and check for updates.

## Notes

If after all this you still get:

> Your device is missing important security and quality fixes.

Or longer:

> Your device is missing important security and quality fixes. Make sure to keep your device on and plugged in so updates can complete.

In such case, a PC fix may be needed.
