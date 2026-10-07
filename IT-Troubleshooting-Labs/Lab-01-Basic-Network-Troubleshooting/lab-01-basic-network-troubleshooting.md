# Lab 01 — Basic Network Troubleshooting

## Scenario

A user reports:

> "My computer can't get on the Internet."

The objective was to troubleshoot the network connection systematically, starting with the network interface and working outward toward the Internet and DNS.

## Lab Environment

* **Operating System:** Ubuntu Server ARM64
* **Virtualization:** UTM
* **Host:** Apple Silicon Mac Mini M1
* **Hostname:** `it-support-lab`
* **Network Interface:** `enp0s1`
* **Network Configuration:** DHCP

## Troubleshooting Process

### 1. Check Network Interface and IP Address

Command:

```bash
ip addr
```

The `enp0s1` interface had an IPv4 address in the `192.168.64.x` range.

**Result:** The system successfully received an IP address through DHCP.

---

### 2. Check the Default Gateway

Command:

```bash
ip route
```

Result:

```text
default via 192.168.64.1 dev enp0s1 proto dhcp src 192.168.64.6 metric 100
```

**Result:** A valid default gateway was configured.

* IP address: `192.168.64.6`
* Default gateway: `192.168.64.1`
* Network interface: `enp0s1`
* Configuration: DHCP

---

### 3. Test the Default Gateway

Command:

```bash
ping -c 4 192.168.64.1
```

Result:

```text
4 packets transmitted
4 packets received
0% packet loss
```

**Result:** The system could communicate successfully with the local gateway.

---

### 4. Test Internet Connectivity

Command:

```bash
ping -c 4 8.8.8.8
```

Result:

```text
4 packets transmitted
4 packets received
0% packet loss
```

**Result:** Direct Internet connectivity was working.

---

### 5. Test DNS Resolution

Command:

```bash
ping -c 4 google.com
```

Result:

```text
4 packets transmitted
4 packets received
0% packet loss
```

**Result:** DNS resolution was working and the destination was reachable.

## Troubleshooting Flow

```text
Network Interface
       ↓
IP Address / DHCP
       ↓
Default Gateway
       ↓
Internet Connectivity
       ↓
DNS Resolution
```

All major connectivity tests succeeded.

## Conclusion

No network connectivity problem was identified in the lab environment.

The troubleshooting process demonstrated a systematic approach to diagnosing a basic Internet connectivity problem.

## Skills Practiced

* Linux command-line troubleshooting
* IPv4 addressing
* DHCP
* Default gateways
* Network interfaces
* Routing
* ICMP/Ping
* DNS
* Internet connectivity testing
* Technical documentation

## Security+ Connections

This lab reinforces the following concepts:

* TCP/IP
* IPv4 addressing
* DHCP
* DNS
* ICMP
* Network troubleshooting
* Layered troubleshooting methodology
* Least-privilege administration

## Commands Used

```bash
ip addr
ip route
ping -c 4 192.168.64.1
ping -c 4 8.8.8.8
ping -c 4 google.com
```

## Portfolio Note

This lab was completed in a controlled Ubuntu Server virtual machine using UTM on an Apple Silicon Mac.

No production systems, credentials, passwords, or sensitive information were used.
