# Playing around with networking

## Concepts to explore

- IP Addressing
- DNS Resolution
- Routing

## IP Addressing

### Commands to check IP addressing

```bash
# Check the IP address of the host
ip addr show

# Check the IP address of the container
hostnamctl
```

## DNS Resolution

### Commands to check DNS resolution

```bash
# Check the local DNS resolution
cat /etc/resolv.conf

# Check the sockets on the host
ss -lt

# How to resolve IPv4 and IPv6 addresses
resolvectl
```
