# My Linux Command Cheat Sheet

I'm keeping this as a reference while learning Linux through my Ubuntu Server home lab. These are commands I've used during guided practice, and I'll update the notes as I understand them better.

## Networking

| Command | What it does | When I'd use it |
|---|---|---|
| `ip -br link` | Shows network interfaces and their status | To see whether my Wi-Fi adapter is UP or DOWN |
| `ip -br addr` | Shows network interfaces and assigned IP addresses | To check whether my server has an IP address |
| `ip -4 addr show wlo1` | Shows IPv4 information for my Wi-Fi interface | To check the Wi-Fi IP address |
| `ping -c 4 1.1.1.1` | Sends four test packets to an external IP address | To test internet connectivity without relying on DNS |
| `getent ahostsv4 ubuntu.com` | Looks up IPv4 addresses for a domain | To check DNS resolution |

## Netplan

| Command | What it does |
|---|---|
| `sudo netplan generate` | Generates network configuration and reports configuration errors |
| `sudo netplan try` | Temporarily applies network settings and allows confirmation or rollback |

## Things I've learned

- Linux network interface names can look like `wlo1`.
- An interface being UP doesn't always mean internet access is working.
- YAML indentation matters when configuring Netplan.
- An IP ping and a DNS lookup test different things.
- `sudo` allows a command to run with administrative privileges.


## SSH and System Administration

| Command | What it does | When I'd use it |
|---|---|---|
| `systemctl status ssh --no-pager` | Checks the SSH service status | To see whether SSH is running |
| `ssh username@server-ip` | Connects to another computer using SSH | To access Ubuntu from Windows |
| `ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub` | Displays the fingerprint of an SSH public host key | To verify the server's identity |
| `uname -s` | Shows the kernel name | To confirm I'm using a Linux environment |

### Things to remember

- SSH stands for Secure Shell.
- A running SSH service doesn't necessarily mean a remote connection will succeed.
- Always verify a new server's host key fingerprint before trusting it.
- Commands entered after an SSH login run on the remote server.
- `systemctl` is used to manage and inspect Linux services.
- I'm still learning how SSH authentication works.


## SSH Session Commands

| Command | What it does |
|---|---|
| `whoami` | Shows which user I'm logged in as |
| `exit` | Closes my current shell session |
| `ssh -v username@server-ip` | Connects through SSH and shows detailed connection information |

### SSH Authentication

SSH can use different methods to verify someone's identity.

- Public key authentication uses cryptographic keys.
- Password authentication uses the account password.
- My SSH client attempted public key authentication before falling back to a password.
- I successfully connected using my Ubuntu account password.

I'm still learning how SSH keys work.

