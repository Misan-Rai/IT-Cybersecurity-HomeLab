# Ubuntu Server Troubleshooting

## Issue 1 — Installer crashed during setup

**Status:** Investigating

### What I was trying to do
I was installing Ubuntu Server on my old HP Pavilion laptop to use it as a dedicated home lab server.

### What happened
During the installation process, the installer crashed and displayed an error report.

The report included the following reference:

`subiquity/apply_autoinstall_config`

### Troubleshooting
- Checked the error report to identify where the installer failed.
- Identified that the installer had crashed rather than simply losing its network connection.
- Planned to reboot the installer and investigate whether the error happens again.

### Resolution
Not resolved yet. I'll update this section once I've identified the cause and completed the installation.

### What I learned
An installer crash is different from a normal network connection failure. Checking the error report is an important first step before attempting a fix.
