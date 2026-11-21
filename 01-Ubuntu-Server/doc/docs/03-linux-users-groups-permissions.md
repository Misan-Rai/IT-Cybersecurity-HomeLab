# Linux User Management and Access Control

## Project overview

As part of my Ubuntu Server home lab, I configured users, groups and directory permissions to simulate how a company might manage access to departmental resources.

I started with a guided IT support department exercise, then configured a separate finance department to practise the commands more independently.

The aim was to understand how Linux controls access and verify that users could only perform actions they were authorised to do.

## Lab environment

- Ubuntu Server running on my HP Pavilion laptop
- SSH access from my main Windows PC
- Administrative account: `misan`
- Two simulated departments: IT Support and Finance

## 1. Creating users and groups

I used Linux user management commands to create department groups and trainee accounts.

```bash
sudo groupadd finance-team
sudo adduser --disabled-password finance-trainee
sudo usermod -aG finance-team finance-trainee
```

I used `id` to inspect the trainee's group memberships and `getent group` to check group information.

```bash
id finance-trainee
getent group finance-team
```

The `-aG` options allow an existing user to be added to a supplementary group without replacing their other supplementary group memberships.

## 2. Configuring the shared directory

I created a directory for the finance department:

```bash
sudo mkdir /srv/finance-team
```

I then changed its group ownership:

```bash
sudo chgrp finance-team /srv/finance-team
```

Finally, I restricted its permissions:

```bash
sudo chmod 750 /srv/finance-team
```

I verified the configuration using:

```bash
ls -ld /srv/finance-team
```

The resulting configuration was:

```text
drwxr-x--- 2 root finance-team 4096 Nov 21 12:38 /srv/finance-team
```

This gives:
- Root: read, write and execute
- Finance team: read and execute
- Others: no access

## 3. Testing access

I tested whether the configured permissions worked using commands executed under different user accounts.

### Test 1 — Authorised access

```bash
sudo -u finance-trainee -- ls -a /srv/finance-team
```

Result:

```text
.
..
```

The trainee could successfully list the directory.

### Test 2 — Denied file creation

```bash
sudo -u finance-trainee -- touch /srv/finance-team/trainee-test.txt
```

Result: Permission denied.

This confirmed that the trainee could access the directory but could not create files directly inside it.

### Test 3 — Unauthorised access

While logged in as `misan`, I ran:

```bash
ls -a /srv/finance-team
```

Result: Permission denied.

My account was not a member of `finance-team`, so ordinary access was denied.

## 4. IT support department exercise

Before the finance department challenge, I completed a guided exercise using:

- Group: `lab-support`
- User: `lab-trainee`
- Directory: `/srv/lab-support`
- Permissions: `750`

I tested successful directory listing, denied file creation and denied access for an unrelated user.

This helped me understand the commands before attempting a second departmental setup.

## 5. Security considerations

The project demonstrates the principle of least privilege.

Rather than allowing everyone full access, permissions were configured according to the users' responsibilities.

I also learned that group ownership and permissions are separate settings. Changing a directory's group owner does not automatically change its permission bits.

## Project status

Both departmental access configurations have been implemented and tested.

The finance configuration was planned from memory, with verification and access testing completed during guided study.
