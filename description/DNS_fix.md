# DNS Failure

## Setup

- **Topology:** PC0 → Switch → Router → Server
- **Network 1:** `192.168.1.0/24`
- **Network 2:** `192.168.2.0/24`
- **Network 3:** `192.168.3.0/24`
- **PC0:** `192.168.1.10/24`
- **PC1:** `192.168.2.10/24`
- **Router G0/0:** `192.168.1.1/24`
- **Router G0/1:** `192.168.2.1/24`
- **Router G0/2:** `192.168.3.1/24`
- **Server:** `192.168.3.20/24`
- **DNS Record:** `test.local` → `192.168.3.20`

## Troubleshooting

I configured the server as a DNS server and created the DNS record `test.local` pointing to `192.168.3.20`.

To simulate a DNS configuration problem, I changed PC0's DNS server address from `192.168.3.20` to `192.168.3.99`.

### Tests

`ping 192.168.3.20`

**Result:** Successful communication.

`ping test.local`

**Result:** Failed — the hostname could not be resolved.

Since PC0 could reach the server using its IP address but not its hostname, I identified the problem as a DNS configuration issue rather than a general network connectivity problem.

## Solution

Changed PC0's DNS server back to:

`192.168.3.20`

The DNS service on the server remained enabled with the record:

`test.local` → `192.168.3.20`

## 

`ping test.local`

**Result:** Successful communication.

## Commands / Tools

- `ping` — test connectivity and verify hostname resolution
- **Server DNS Service** — configure the DNS service and records
- **Packet Tracer IP Configuration** — inspect and correct the DNS server address
- `show ip interface brief` — check router interface status and IP addresses

## What I Learned

This lab helped me understand the difference between network connectivity and DNS resolution. I practiced comparing a direct IP ping with a hostname ping to identify where the problem was occurring. I also gained experience configuring a DNS record, troubleshooting an incorrect DNS server address, and verifying the fix after correcting the configuration.
