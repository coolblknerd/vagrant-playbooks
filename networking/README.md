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
```

## Hostnames and DNS Resolution

- Hostnames are human-readable names that are mapped to IP addresses.
- DNS (Domain Name System) is a hierarchical system that translates human-readable domain names into IP addresses.
- DNS resolution is the process of converting a hostname into an IP address.
- DNS servers are responsible for resolving domain names into IP addresses.
- LLMNR (Link-Local Multicast Name Resolution) is a protocol that allows both IPv4 and IPv6 hosts to perform name resolution on the local link without the need for a DNS server.
- The `/etc/hosts file` is used to map hostnames to IP addresses locally.
- The `/etc/resolv.conf` file is used to configure the DNS servers that the host will use for name resolution.
- The `/etc/nsswitch.conf` file is used to configure the name service switch, which determines how hostnames are resolved.
- The `/etc/systemd/resolved.conf` file is used to configure the systemd-resolved service, which provides network name resolution to local applications.

### Commands to check DNS resolution

```bash
# Check the hostname of the host
hostname

# Manage hostnames
hostnamectl

# Check the local DNS resolution
cat /etc/resolv.conf

# Check the sockets on the host
ss -lt

# How to resolve IPv4 and IPv6 addresses
resolvectl
```

## NTP Client and Time Synchronization

- By default, Ubuntu makes use of the NTP client-only systemd-timesyncd. This gives systems a smaller footprint and improved security.
- The NTP client is managed with `timedatectl` and is enabled by default.
- NTP (Network Time Protocol) is a protocol used to synchronize the clocks of systems
- NTP clients are used to synchronize the time of a host with an NTP server.
- NTP servers are responsible for providing accurate time to NTP clients.
- The `/etc/systemd/timesyncd.conf` file is used to configure the systemd-timesyncd service, which provides network time synchronization to local applications.

### Commands to check NTP configuration

```bash
# Check the NTP configuration
timedatectl

# Set the timezone
timedatectl set-timezone <timezone>

# Set the NTP synchronization
timedatectl set-ntp true

# Check the NTP service
systemctl status systemd-timesyncd.service

# Check the Timesync status
timedatectl timesync-status

# Show the Timesync details
timedatectl show-timesync
```

## Resources

- [LLMNR Poisoning](https://tcm-sec.com/llmnr-poisoning-and-how-to-prevent-it/)