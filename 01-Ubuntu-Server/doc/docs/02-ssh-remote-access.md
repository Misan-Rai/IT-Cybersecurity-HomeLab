# Setting Up SSH Remote Access

## What I wanted to achieve

After getting my Ubuntu Server connected to Wi-Fi, I wanted to access it from my main Windows PC instead of using the laptop's keyboard and screen every time.

## What is SSH?

SSH stands for Secure Shell. It lets you securely access and manage another computer over a network using a terminal.

## What I did

I first checked whether the SSH service was already running:

```bash
systemctl status ssh --no-pager
```

It showed that the service was active, so I didn't need to install it again.

I checked my Ubuntu Server's Wi-Fi IP address:

```bash
ip -4 -br addr show wlo1
```

Then, from Windows PowerShell, I connected using:

```powershell
ssh <ubuntu-username>@<server-ip>
```

On my first connection, SSH showed a host key fingerprint. I checked it against the fingerprint on the Ubuntu Server using:

```bash
ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub
```

After confirming the fingerprints matched, I accepted the connection.

## A problem I encountered

I originally tried running `uname -s` in Windows PowerShell and received a command-not-recognised error.

I later realised I hadn't entered the Ubuntu environment yet. Once I connected successfully through SSH, the command worked and returned `Linux`.

This helped me understand that commands run on different computers depending on whether I'm using my local terminal or a remote SSH session.

## What I've learned so far

- SSH lets me control my server remotely.
- Linux services can be checked using `systemctl`.
- A server's SSH fingerprint should be verified before trusting a first connection.
- I need to pay attention to whether I'm using Windows PowerShell or a Linux shell.
- Troubleshooting starts with understanding where the problem is happening.

## What I still need to learn

- How SSH authentication works and why my connection didn't request a password.
- How to use SSH keys confidently.
- How to secure and maintain SSH access.
- How to reconnect and troubleshoot independently without step-by-step guidance.

## Next steps

Investigate my SSH authentication method, practise reconnecting, and learn basic Linux administration.
