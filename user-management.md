# Linux User and Group Management

This document describes user and group management commands practiced in my Ubuntu Server virtual lab.

## 1. Identify the Current User

```bash
whoami
```

Displays the username of the current session.

```bash
id
```

Displays the current user's UID, primary group, and supplementary groups.

## 2. Create a User

```bash
sudo useradd -m testuser
```

Creates a user named `testuser` and creates a home directory for the user.

The `-m` option creates the home directory if needed.

## 3. Set a Password

```bash
sudo passwd testuser
```

Sets or changes the password for `testuser`.

## 4. Create a Group

```bash
sudo groupadd developers
```

Creates a group named `developers`.

## 5. Add a User to a Supplementary Group

```bash
sudo usermod -aG developers testuser
```

Adds `testuser` to the `developers` group.

- `-a` appends the group without removing existing supplementary group memberships.
- `-G` specifies supplementary groups.

## 6. Verify Group Membership

```bash
id testuser
```

Displays the UID, primary group, and supplementary groups of `testuser`.

## 7. Delete a User

```bash
sudo deluser testuser
```

Deletes the user account. This command does not request removal of the user's home directory.

To delete the account and its home directory:

```bash
sudo deluser --remove-home testuser
```

Use account deletion commands only for test accounts that you are authorized to remove.

## Key Takeaways

- `useradd` creates user accounts.
- `passwd` manages passwords.
- `groupadd` creates groups.
- `usermod -aG` adds a user to supplementary groups.
- `id` verifies user and group information.
- `deluser` removes user accounts.

These exercises are intended for a local Ubuntu Server lab.
