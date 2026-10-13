# Lab 02 — DNS Troubleshooting

## Scenario

A user reports:

> "My computer is connected to the network, but websites are not working."

The goal of this lab is to determine whether the problem is network connectivity or DNS name resolution.

## Lab Environment

- Ubuntu Server ARM64
- UTM virtual machine
- Hostname: `it-support-lab`
- User: `kevin`
- Network: DHCP
- Tools: `nslookup` and `ping`

## Step 1 — Test DNS Resolution

Command:

```bash
nslookup google.com