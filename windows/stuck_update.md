## My problem

In Windows 11 Home, a specific update wouldn't install for years, whilst other updates get installed regularly.

I keep getting a notification about the need to update Windows and it leads to the following message:

> Your device is missing important security and quality fixes. Make sure to keep your device on and plugged in so updates can complete.

## The cause of the problem

Probably, the cause of the problem is that the specific personal computer I work with is a bit old, a **Dell Latitude 5580** from year 2017.

## What I have tried to solve the problem

### Hiding the update icon in the system tray

Just to make the `system tray` icon of update notifications go away, I right-clicked on the icon and then left-clicked on "Hide for now". This made the notification go away, but only until next reset, then it came back to appear.

### Run Powershell as Administrator

```powershell
Install-Module PSWindowsUpdate -Force
Import-Module PSWindowsUpdate
```

If asked to install *NuGet* than install it because NuGet is a Microsoft package manager required to download PowerShell modules like `PSWindowsUpdate`. It's safe and necessary in this context.

### Hiding the update

```powershell
Hide-WindowsUpdate -Title "hp usb 12/10/2018 12:00 AM - 49.0.4411.18331"
```

* If getting an error about the lack of ability to run scripts due to to Powershell execution policy, then to  proceed safely temporarily allow scripts for your current session only:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then run the command to hide the update.

### Confirm result

```powershell
Get-WindowsUpdate -IsHidden
```

Something like this sould be put out:

```
ComputerName Status     KB          Size Title
------------ ------     --          ---- -----
X          -D--H--                14MB UPDATE_TITLE_COMES_HERE
```

`-D--H--` means "Declined" and "Hidden".

### Reset Windows update components

Still getting:

> Your device is missing important security and quality fixes. Make sure to keep your device on and plugged in so updates can complete.

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

No errors where given.

### Open `Run` and execute the following

```
ms-settings:troubleshoot
```

Theen do:

**Other troubleshooters** > **Windows Update** > **Run** (click "Run" button there).

### Open CMD as Administrator

```cmd
usoclient StartScan
```

No output was given.

Or:

```cmd
wuauclt /detectnow /updatenow
```

No output was given.

### Deployment Image Servicing and Management (DISM)

```cmd
DISM /Online /Cleanup-Image /CheckHealth
DISM /Online /Cleanup-Image /ScanHealth
DISM /Online /Cleanup-Image /RestoreHealth
```

No corruption was found anywhere.

### Windows update troubleshooter finds a problem but doesn't fix it.

Open **Settings** > **System** > **Recovery**, then under Recovery options, click **Reset this PC** > **Remove everything** > **Local reinstall**.

This fully resets Windows to factory state without needing a product key. Windows 11 will auto-activate after reinstall since the key is tied to the hardware.

## How to solve that problem?

Short answer without waffling. No emojis and no colorful characters. Just a short explanation about what to do.
