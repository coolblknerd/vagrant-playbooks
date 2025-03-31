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

## Resources

- [LLMNR Poisoning](https://tcm-sec.com/llmnr-poisoning-and-how-to-prevent-it/)