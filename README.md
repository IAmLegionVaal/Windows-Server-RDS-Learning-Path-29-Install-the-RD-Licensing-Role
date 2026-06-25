# Windows Server RDS Learning Path 29 — Install the RD Licensing Role

**Level:** Intermediate · **Module:** 29/70

## Goal
Install the RD Licensing role and management tools on the selected lab server.

## Setup
1. Select the license-server host; the compact lab may use RDS01.
2. In RDS Overview select **+ RD Licensing**, or add the role service through Server Manager.
3. Allow required restart.
4. Open RD Licensing Manager.
5. Add the server to the Terminal Server License Servers group when required.
6. Do not install CAL packs not legitimately owned.

```powershell
Get-WindowsFeature RDS-Licensing,RDS-Licensing-UI
Get-Service TermServLicensing
Get-ADGroupMember 'Terminal Server License Servers'
Get-WinEvent -LogName 'Microsoft-Windows-TerminalServices-Licensing/Operational' `
  -MaxEvents 50 -ErrorAction SilentlyContinue
```

## Evidence
Capture role installation, service state, AD group membership, Licensing Manager screenshot and events under `evidence/`.

## Troubleshooting
If management tools are missing, install `RDS-Licensing-UI`. For service or registration errors, verify domain connectivity, DNS and permissions.

## Security and compliance
RDS Session Hosts require appropriate RDS CALs for users/devices. The lab guide does not bypass or reset licensing.

## Rollback
Remove the role only after the deployment no longer points to this license server.

## Next
`Windows-Server-RDS-Learning-Path-30-Configure-the-RDS-Licensing-Mode`
