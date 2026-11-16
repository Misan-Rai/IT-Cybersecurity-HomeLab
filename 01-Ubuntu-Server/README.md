# Ubuntu Home Server

## About the Project

I've got an old HP Pavilion laptop that I no longer use, so I decided to turn it into a home server rather than leave it sitting around.

I'm currently learning IT and cybersecurity, and I thought building my own server would be a good way to get some hands-on experience with Linux, networking and managing different services.

My plan is to use this laptop to run things like Docker, Pi-hole and monitoring tools. I'll be documenting the setup here, including anything that goes wrong along the way.

## Hardware

| Equipment | Details |
|---|---|
| Laptop | HP Pavilion 14-ce3606sa |
| RAM | 8GB |
| Storage | 512GB Intel SSD |
| Operating system | Ubuntu Server LTS (installation in progress) |
| Router | Virgin Media Hub 5 |
| Network | Wi-Fi |

## Setting Up Ubuntu Server

I downloaded Ubuntu Server and used Rufus to create a bootable USB drive.

I then booted the laptop from the USB using the HP boot menu (Esc followed by F9).

For the installation, I've chosen the standard Ubuntu Server option.

### Storage Setup

I'm planning to use the laptop's entire 512GB SSD since I won't be using its previous operating system anymore.

I've also selected LVM (Logical Volume Manager). From what I've learned so far, LVM makes it easier to manage and resize storage volumes later on.

The storage changes haven't been confirmed yet.

## Problems I've Run Into

### Installer crashing

My first attempt at installing Ubuntu didn't go to plan.

While I was setting up the Wi-Fi connection, the installer crashed and displayed an error report. I tried restarting the laptop, but it got stuck on the rebooting screen, so I had to shut it down manually.

On my second attempt, I skipped the Wi-Fi setup and managed to get past the point where it previously crashed.

I'm still not sure exactly what caused the issue. I'll update this once the installation is finished.

I've also recorded the issue in my [troubleshooting notes](troubleshooting.md).

## Progress

- [x] Checked the laptop's hardware
- [x] Created a bootable Ubuntu Server USB
- [x] Booted into the Ubuntu installer
- [x] Selected the standard Ubuntu Server installation
- [x] Got past the previous installer crash
- [ ] Finish installing Ubuntu Server
- [ ] Configure Wi-Fi
- [ ] Set up SSH for remote access
- [ ] Install Docker
- [ ] Deploy my first service

## What I've Learned

So far, I've learned how to create a bootable USB, boot a computer using UEFI and identify the correct disk during a Linux installation.

I've also started learning about LVM and why it might be useful when managing storage on a server.

I'll keep updating this section as I work through the project.
