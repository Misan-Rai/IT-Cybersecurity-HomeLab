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

## Things I want to practise again

- Identifying my Wi-Fi interface without guidance
- Checking whether my server has an IP address
- Troubleshooting a failed internet connection
- Explaining what DNS does in my own words
