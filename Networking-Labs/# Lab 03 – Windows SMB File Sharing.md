# Lab 03 – Windows SMB File Sharing

## Objective
Configure a shared folder on Windows 11 and access it remotely from an Ubuntu Server using SMB.

## Lab Environment
- Windows 11 Pro VM: `192.168.64.9`
- Ubuntu Server VM: `192.168.64.6`
- Active Directory Domain: `butlerlab.local`
- Domain User: `labuser`

## Windows Configuration
1. Created a folder named `LabShare` on the C: drive.
2. Opened folder Properties → Sharing → Advanced Sharing.
3. Enabled **Share this folder**.
4. Configured share permissions for Everyone with Full Control (lab exercise only).

## Ubuntu Connection Test

Used the following command to list available Windows shares:

```bash
smbclient -L 192.168.64.9 -U 'BUTLERLAB\labuser'
```

Connected directly to the shared folder:

```bash
smbclient //192.168.64.9/LabShare -U 'BUTLERLAB\labuser'
```

Authenticated using the Windows domain account password.

## Results
- Successfully connected from Ubuntu to the Windows SMB share.
- Received the interactive `smb: \>` prompt.
- Confirmed SMB authentication and network access.

## Skills Practiced
- SMB file sharing
- Windows folder sharing
- Domain authentication
- Linux-to-Windows connectivity
- Network share permissions
- Command-line troubleshooting

## Security Note
Full Control for Everyone was used for this isolated lab exercise. In a production environment, permissions should follow the principle of least privilege.
