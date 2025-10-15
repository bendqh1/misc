## 1) Run Powershell as Administrator

```powershell
Install-Module PSWindowsUpdate -Force
Import-Module PSWindowsUpdate
```

* If asked to install NuGet:<br>
NuGet is a Microsoft package manager required to download PowerShell modules like PSWindowsUpdate. It's safe and necessary in this context.

## 2) Hide a given update

```powershell
Hide-WindowsUpdate -Title "UPDATE_TITLE_COMES_HERE_EXACTLY_AS_WRITTEN"
```

* If getting an error about the lack of ability to run scripts due to to Powershell execution policy.<br>
To proceed safely, temporarily allow scripts for your current session only:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

And only then run the command to hide the update.

## Confirm result

```powershell
Get-WindowsUpdate -IsHidden
```

Something like this sould be put out:

```
ComputerName Status     KB          Size Title
------------ ------     --          ---- -----
X          -D--H--                14MB UPDATE_TITLE_COMES_HERE_EXACTLY_AS_WRITTEN
```

`-D--H--` means "Declined" and "Hidden".

## 4) Restart

Restart the PC and check for updates.

## If it's not enough

If after all this you still get:

> Your device is missing important security and quality fixes. Make sure to keep your device on and plugged in so updates can complete.

### 1) Open Powershell and reset Windows Update components

```powershell
net stop wuauserv
net stop cryptSvc
net stop bits
net stop msiserver
ren C:\Windows\SoftwareDistribution SoftwareDistribution.old
ren C:\Windows\System32\catroot2 catroot2.old
net start wuauserv
net start cryptSvc
net start bits
net start msiserver
```

### 2) Open `Run` and execute the following

```
ms-settings:troubleshoot
```

Theen do:

**Other troubleshooters** > **Windows Update** > **Run** (click "Run" button there).

### 3) Open CMD as Administrator

```cmd
usoclient StartScan
```

Or:

```cmd
wuauclt /detectnow /updatenow
```

## If all of this didn't help

```cmd
DISM /Online /Cleanup-Image /CheckHealth
DISM /Online /Cleanup-Image /ScanHealth
DISM /Online /Cleanup-Image /RestoreHealth
```

No corruption was found anywhere.

1. Restart the PC and after that:<br>
2. Run Windows Update Troubleshooter again via **Settings** > **System** > **Troubleshoot** > **Other troubleshooters**.
3. Do `usoclient StartScan`.
