## Setup

- **Topology:** PC0 → Switch → PC1
- **PC0:** `192.168.1.10/24`
- **PC1:** `192.168.1.20/24`
- Same subnet, so no default gateway was required.

## Troubleshooting

I changed PC0's IP to `192.168.2.10/24` to simulate an incorrect network configuration.

### Test

`ping 192.168.1.20`

**Result:** Failed.

I checked the IP configuration and identified that PC0 was on `192.168.2.0/24` while PC1 was on `192.168.1.0/24`.

## Resolution

Changed PC0 back to:

- **IP Address:** `192.168.1.10`
- **Subnet Mask:** `255.255.255.0`

## Verification

`ping 192.168.1.20`

**Result:** Successful communication.

## Commands / Tools

- `ping` — test connectivity between devices
- **Packet Tracer IP Configuration** — inspect and correct addressing

## What I Learned

This lab helped me understand how IP addressing affects communication between devices. I practiced using `ping` to identify connectivity problems and comparing IP addresses and subnet masks to find the cause. 
