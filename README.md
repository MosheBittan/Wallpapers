Open CMD or PowerShell as Administrator and run: reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /v NoAutoUpdate /t REG_DWORD /d 1 /f This is the policy-level 'do not auto update' flag and works on Home and Pro.

Still in the elevated prompt, run these three commands (Start=4 means Disabled). The second one is the medic service — this is the step that makes it permanent: reg add "HKLM\SYSTEM\CurrentControlSet\Services\wuauserv" /v Start /t REG_DWORD /d 4 /f reg add "HKLM\SYSTEM\CurrentControlSet\Services\WaaSMedicSvc" /v Start /t REG_DWORD /d 4 /f reg add "HKLM\SYSTEM\CurrentControlSet\Services\UsoSvc" /v Start /t REG_DWORD /d 4 /f Use the registry, not services.msc — the medic service shows 'Access Denied' in the normal Services window.

