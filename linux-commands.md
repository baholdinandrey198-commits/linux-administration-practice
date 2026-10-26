# Linux Command-Line Practice

This document contains Linux commands practiced in my Ubuntu Server virtual lab.

## 1. Navigation

### Show the current directory

```bash
pwd
```

Displays the path of the current working directory.

### List files and directories

```bash
ls -la
```

Displays files, including hidden files, with detailed information.

### Navigate to the home directory

```bash
cd "$HOME"
```

Changes the current directory to the user's home directory.

## 2. File and Directory Management

### Create a directory

```bash
mkdir practice
```

Creates a directory named `practice`.

### Create an empty file

```bash
touch notes.txt
```

Creates an empty file named `notes.txt` if it does not already exist.

### Find files by name

```bash
find "$HOME" -name "notes.txt"
```

Searches for files named `notes.txt` inside the user's home directory.

## 3. Reading and Writing Files

### Display the first lines of a file

```bash
head notes.txt
```

Displays the first 10 lines by default.

### Append text to a file

```bash
echo "Linux practice" >> notes.txt
```

Adds a line to the end of the file without overwriting existing content.

## 4. User Management

### Display the current user

```bash
whoami
```

Prints the username of the current session.

### Display user and group IDs

```bash
id
```

Displays the current user's UID, primary group, and supplementary groups.

## 5. System Administration

### Display operating system information

```bash
cat /etc/os-release
```

Shows information about the installed Linux distribution.

### Display disk usage

```bash
df -h
```

Shows filesystem space usage in a human-readable format.

### Display memory usage

```bash
free -h
```

Displays memory and swap usage.

## 6. Network Troubleshooting

### Display IP addresses

```bash
ip address
```

Shows network interfaces and their IP addresses.

### Test network connectivity

```bash
ping -c 4 8.8.8.8
```

Sends four ICMP packets to test connectivity to a public IP address.

## 7. SSH

### Connect to a remote server

```bash
ssh username@server_ip
```

Connects to a remote server using SSH. Replace `username` and `server_ip` with the actual values.

**Note:** Commands are documented for learning purposes. Some commands require appropriate permissions or adjustments for the environment.
