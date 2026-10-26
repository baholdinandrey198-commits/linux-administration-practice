# Linux Networking and SSH Practice

This document covers basic network diagnostics and SSH access in my Ubuntu Server virtual lab.

## 1. Display Network Interfaces

```bash
ip address
```

Displays network interfaces and their IP addresses.

```bash
ip route
```

Displays the routing table, including the default route when configured.

## 2. Test Network Connectivity

```bash
ping -c 4 8.8.8.8
```

Sends four ICMP packets to test connectivity to a public IP address.

```bash
getent hosts ubuntu.com
```

Checks whether the system can resolve a hostname to an address.

## 3. Inspect Listening Ports

```bash
sudo ss -tulpn
```

Displays listening TCP and UDP sockets and, where permitted, associated process information.

## 4. Check SSH Service Status

```bash
sudo systemctl status ssh
```

Displays the status of the SSH service on Ubuntu.

```bash
sudo systemctl is-enabled ssh
```

Checks whether the SSH service is configured to start automatically at boot.

## 5. Test SSH Configuration

```bash
sudo sshd -t
```

Checks the SSH server configuration for syntax errors. No output usually indicates that the configuration passed this check.

## 6. Connect to a Remote Server

```bash
ssh username@server_ip
```

Connects to a remote server. Replace `username` and `server_ip` with the appropriate values.

## 7. VirtualBox Networking Notes

In my lab, Ubuntu Server runs inside Oracle VirtualBox.

Network behavior depends on the selected VirtualBox adapter mode and any configured port forwarding rules.

When using NAT with SSH port forwarding, a connection from the Windows host may look like this:

```powershell
ssh -p 2222 andrey@127.0.0.1
```

This example assumes that host port `2222` forwards to port `22` on the Ubuntu virtual machine.

## Key Takeaways

- `ip address` displays interface addresses.
- `ip route` displays routing information.
- `ping` tests IP connectivity.
- `getent hosts` helps check name resolution.
- `ss` displays socket information.
- `systemctl` helps inspect and manage services.
- SSH provides encrypted remote access.

These commands are documented for learning and troubleshooting in a test environment.
