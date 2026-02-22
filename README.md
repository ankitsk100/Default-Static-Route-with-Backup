# Default Static Route with Backup (Floating Static Route)

---

## Project Overview

This project demonstrates WAN redundancy using:

- Primary Default Static Route
- Backup Default Route (Floating Static Route)

The backup route is configured with a higher Administrative Distance (130) so it becomes active only when the primary route fails.

---

## Network Details

### LAN
Network: `192.168.1.0/24`

| Device | IP Address |
|--------|------------|
| Router2 | 192.168.1.1 |
| PC2 | 192.168.1.3 |
| PC3 | 192.168.1.4 |

### WAN Links

| Link | Subnet | Router2 | ISP |
|------|--------|---------|-----|
| Router2 ↔ ISP-1 | 200.100.50.0/30 | 200.100.50.1 | 200.100.50.2 |
| Router2 ↔ ISP-2 | 200.100.50.4/30 | 200.100.50.5 | 200.100.50.6 |

---

## Primary Route

ip route 0.0.0.0 0.0.0.0 200.100.50.2

---
## backup Route
ip route 0.0.0.0 0.0.0.0 200.100.50.6 130

## ISP Return Route

ISP - 1
ip route 192.168.1.0 255.255.255.0 200.100.50.1

ISP - 2
ip route 192.168.1.0 255.255.255.0 200.100.50.5

---

## Verrification

show ip route

show ip route static

 
## Failover Test 

conf t

interface g0/1

shutdown

end

## Tracert From PC 

tracert 8.8.8.8


