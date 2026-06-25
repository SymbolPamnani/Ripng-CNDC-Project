RIPng IPv6 Routing Configuration
Overview
IPv6-based routed network using RIPng in Cisco Packet Tracer.
3 routers interconnected via serial WAN links enable cross-subnet communication.

Technologies: IPv6, RIPng, Serial DCE, ICMPv6

Topology
text
PC0 ─── R0 ─── R1 ─── R2 ─── PC2
               │
              PC1
Device	IPv6 Address
PC0	2001:DB8:1:0:2E0:B0FF:FE86:5EA7
PC1	2001:DB8:2:0:20A:41FF:FEE2:D773
PC2	2001:DB8:3:0:2E0:A3FF:FE06:6410
Router Config (R0)
cisco
ipv6 unicast-routing
interface g0/0/0
 ipv6 address 2001:db8:1::1/64
 ipv6 rip RIPNG enable
 no shutdown
interface serial0/1/0
 ipv6 address 2001:db8:12::1/64
 ipv6 rip RIPNG enable
 clock rate 64000
 no shutdown
ipv6 router rip RIPNG
(Similar config on R1 and R2)

Testing
cmd
ping 2001:DB8:2:0:20A:41FF:FEE2:D773   # PC0 → PC1 ✅
ping 2001:DB8:3:0:2E0:A3FF:FE06:6410   # PC0 → PC2 ✅
Result: 0% packet loss — cross-subnet communication working.

Files
RIPng_Project.pkt — Packet Tracer file

Report.pdf — Full project report

/screenshots — Network topology and test results
