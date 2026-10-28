# Lab 03: IP Configuration and Network Connectivity Troubleshooting

## Objective
Practice identifying network interfaces, interpreting IP configuration, locating the default gateway, and testing network connectivity and DNS resolution in an Ubuntu Server virtual machine.

## Lab Environment
- **Host computer:** Mac mini M1
- **Virtualization software:** UTM
- **Operating system:** Ubuntu Server ARM64
- **Network interface:** `enp0s1`

## Commands Practiced

| Command | Purpose |
|---|---|
| `ip addr` | Displays network interfaces and IP addresses |
| `ip route` | Displays routing information and the default gateway |
| `ping -c 4 192.168.64.1` | Tests connectivity to the default gateway |
| `ping -c 4 8.8.8.8` | Tests connectivity to an external IP address |
| `ping -c 4 google.com` | Tests hostname resolution and connectivity |

## Network Configuration

| Setting | Observed Value |
|---|---|
| Network interface | `enp0s1` |
| IPv4 address | `192.168.64.6` |
| Subnet prefix | `/24` |
| Subnet mask | `255.255.255.0` |
| Network address | `192.168.64.0` |
| Broadcast address | `192.168.64.255` |
| Default gateway | `192.168.64.1` |
| Address assignment | DHCP |

## Connectivity Test Results

### Test 1: Default Gateway
**Command:** `ping -c 4 192.168.64.1`

**Result:** 4 packets transmitted, 4 received, 0% packet loss.

**Conclusion:** The virtual machine successfully communicated with its configured default gateway.

### Test 2: External IP Connectivity
**Command:** `ping -c 4 8.8.8.8`

**Result:** 4 packets transmitted, 4 received, 0% packet loss.

**Conclusion:** The virtual machine successfully reached an external IP address.

### Test 3: DNS and Hostname Connectivity
**Command:** `ping -c 4 google.com`

**Result:** 4 packets transmitted, 4 received, 0% packet loss.

**Conclusion:** The hostname resolved and the virtual machine received replies. DNS resolution and connectivity worked during this test.

## Troubleshooting Workflow
1. Inspect network interfaces with `ip addr`.
2. Verify the assigned IP address and subnet.
3. Inspect the routing table with `ip route`.
4. Test connectivity to the default gateway.
5. Test connectivity to an external IP address.
6. Test a hostname to check DNS resolution and connectivity.
7. Use the results to narrow down the likely source of a network issue.

## Key Learning
A systematic troubleshooting process helps isolate network problems. Successful gateway, external IP, and hostname tests provide evidence that basic network connectivity and DNS resolution were working in this lab. A successful ping does not guarantee that every website or application service is functioning.

## Portfolio Note
This lab was completed in a personal Ubuntu Server virtual machine and demonstrates practical command-line networking and troubleshooting skills.
