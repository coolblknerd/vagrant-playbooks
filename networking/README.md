# Playing around with networking

## Concepts to explore

- IP Addressing
- DNS Resolution
- Routing

## IP Addressing

### Commands to check IP addressing

```bash
# Check the IP address of the host
$ ip addr show
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
$ hostname

# Manage hostnames
$ hostnamectl

# Check the local DNS resolution
$ cat /etc/resolv.conf

# Check the sockets on the host
$ ss -lt

# How to resolve IPv4 and IPv6 addresses
$ resolvectl
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
$ timedatectl

# Set the timezone
$ timedatectl set-timezone <timezone>

# Set the NTP synchronization
$ timedatectl set-ntp true

# Check the NTP service
$ systemctl status systemd-timesyncd.service

# Check the Timesync status
$ timedatectl timesync-status

# Show the Timesync details
$ timedatectl show-timesync
```

## Routing

- Routing is the process of forwarding packets from one network to another.
- Routers are devices that forward packets between networks.
- The routing table is a data structure that contains information about the routes to different networks.
- The routing table is used by the kernel to determine the best route for a packet.
- If you want to change a hosts to a router, you need to enable IP forwarding.
  - The `/etc/sysctl.conf` file is used to configure kernel parameters at runtime.
  - Updating `net.ipv4.ip_forward` to `1` will enable IP forwarding.
  - Updating `net.ipv6.conf.all.forwarding` to `1` will enable IPv6 forwarding.
  - The changes can be applied immediately using `sysctl -p`.

### Commands to check routing

```bash
# Check the routing table
$ ip route show

# Check the system routing
$ sysctl -ar ip_forward
```

## Firewalls

- Firewalls are used to control the flow of traffic between networks.
- Firewalls can be implemented in hardware or software.
- Firewalls can be used to block or allow traffic based on rules.
- Understanding ports and protocols is important for configuring firewalls since ports are like doors to a building, and protocols are the rules that govern how data is transmitted over those doors.
- In order to connect to a service across a network, the client must know the IP address of the server and the port number on which the service is listening.
  - The service has to be started and listening on the port.
  - Ports can be managed with either the TCP or UDP protocols.
  - It's always good to audit a system by checking the ports that are open and listening for connections.
  - `nmap` is a powerful tool for network exploration and security auditing.

### Commands to check firewalls


## Resources

- [LLMNR Poisoning](https://tcm-sec.com/llmnr-poisoning-and-how-to-prevent-it/)