# Wrong Gateway and Router Interface

## Setup

- **Topology:** PC0 → Switch1 → Router → Switch2 → PC1
- **Network 1:** `192.168.1.0/24`
- **Network 2:** `192.168.2.0/24`
- **PC0:** `192.168.1.10/24`
- **PC1:** `192.168.2.10/24`
- **Router G0/0:** `192.168.1.1/24`
- **Router G0/1:** `192.168.2.1/24`

## Troubleshooting

I changed PC0's default gateway to `192.168.1.99` to simulate an incorrect gateway configuration.

### Test: `ping 192.168.2.10`

**Result:** Failed.

I checked PC0's IP configuration and identified that the default gateway was incorrect. I also checked the router interfaces using:

```text
show ip interface brief
```

G0/0 was **administratively down**, which prevented communication between the two networks.

## Resolution

Changed PC0's default gateway to:

```text
192.168.1.1
```

Enabled the router's G0/0 interface:

```text
interface gigabitEthernet 0/0
no shutdown
```

The router interfaces were then up and operational.

## Verification

```text
ping 192.168.2.10
```

**Result:** Successful communication.

## Commands / Tools

- `ping` — test connectivity between networks
- `show ip interface brief` — check router interface status and IP addresses
- `no shutdown` — enable a router interface
- Packet Tracer IP Configuration — inspect and correct the default gateway

## What I Learned

This lab helped me understand the role of the default gateway when communicating with devices on another network. I practiced checking router interface status with `show ip interface brief` and identifying when an interface was administratively down. I also gained experience correcting both a gateway configuration and a router interface problem, then verifying the connection with `ping`.
