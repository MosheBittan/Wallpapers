Open CMD or PowerShell as Administrator and run: reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /v NoAutoUpdate /t REG_DWORD /d 1 /f This is the policy-level 'do not auto update' flag and works on Home and Pro.

Still in the elevated prompt, run these three commands (Start=4 means Disabled). The second one is the medic service — this is the step that makes it permanent: reg add "HKLM\SYSTEM\CurrentControlSet\Services\wuauserv" /v Start /t REG_DWORD /d 4 /f reg add "HKLM\SYSTEM\CurrentControlSet\Services\WaaSMedicSvc" /v Start /t REG_DWORD /d 4 /f reg add "HKLM\SYSTEM\CurrentControlSet\Services\UsoSvc" /v Start /t REG_DWORD /d 4 /f Use the registry, not services.msc — the medic service shows 'Access Denied' in the normal Services window.



How to Prevent and Fix It
Instead of manually resetting the wallpaper every time, you can address the root causes at the protocol or system level.

Force Wallpaper in the RDP Client
Before clicking "Connect" in your Remote Desktop Connection (mstsc.exe):

Click Show Options.

Go to the Experience tab.

Check the box for Desktop background. (Note: This forces the wallpaper to load, but slightly increases bandwidth usage).

Disable the Restrictive Group Policy
If checking the box in the client doesn't work, the destination machine or VM might have a Group Policy overriding your request.

On the remote machine, open gpedit.msc.

Navigate to: Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Remote Session Environment.

Locate Enforce Removal of Remote Desktop Wallpaper.

Set it to Disabled or Not Configured.
