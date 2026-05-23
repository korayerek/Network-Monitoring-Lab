# Network Monitoring and Troubleshooting Lab

## Overview

This project is an enterprise-style network monitoring and troubleshooting lab built in Cisco Packet Tracer.

The goal of this lab was to simulate real-world network troubleshooting scenarios and practice operational fault isolation using CLI tools, syslog monitoring, VLAN troubleshooting, and Layer 2 / Layer 3 diagnostics.

The environment includes multilayer switching, VLAN segmentation, centralized syslog monitoring, SSH remote management, ACL troubleshooting, and inter-VLAN routing.

Several realistic network problems were intentionally created and resolved using a structured troubleshooting workflow.

---

## Network Topology

![Topology](koray-erek-network-monitoring-lab-topology.png)

---

## Technologies Used

- Cisco Packet Tracer
- Cisco Catalyst 3650 Multilayer Switch
- Cisco Catalyst 2960 Switches
- VLANs
- Inter-VLAN Routing
- Trunking
- Syslog Monitoring
- SSH
- ACLs
- Layer 2 Troubleshooting
- Layer 3 Troubleshooting
- Fault Isolation


---

## Network Design

The lab consists of:

- 1 Multilayer Core Switch
- 2 Access Switches
- Multiple End Devices
- Centralized Syslog Server
- User VLAN
- Monitoring / Server VLAN
- Management VLAN

The multilayer switch provides inter-VLAN routing while the access switches provide endpoint connectivity and centralized monitoring integration.

---

## VLAN Plan

| VLAN | Purpose |
|------|----------|
| VLAN 10 | Users |
| VLAN 20 | Monitoring / Server |
| VLAN 30 | Management |
| VLAN 99 | Native VLAN |

---

## Monitoring Features

- Centralized syslog monitoring
- SSH remote management
- Interface event logging
- Connectivity verification
- VLAN and trunk troubleshooting
- ACL troubleshooting
- Fault isolation workflow

---

## Centralized Syslog Monitoring

The lab uses a centralized syslog server to collect logs from network devices.

Syslog monitoring was used to:

- Verify interface failures
- Detect connectivity events
- Validate troubleshooting scenarios
- Confirm fault restoration after fixes

![Centralized Syslog Monitoring](centralized-syslog-monitoring.png)

---

# Scenario 1 — Interface Shutdown Troubleshooting

## Problem

PC1 lost network connectivity because an access interface on SW2-Users was administratively shut down.

## Troubleshooting Process

- Ping testing
- Interface status verification
- Syslog analysis
- Interface recovery validation

## Root Cause

FastEthernet0/1 on SW2-Users was administratively shut down.

## Resolution

The interface was re-enabled using the `no shutdown` command.

### Screenshots

![Ping Failure](s1-ping-failure.png)

![Interface Down](s1-interface-down.png)

![Syslog Event](s1-syslog-event.png)

![Connectivity Restored](s1-connectivity-restored.png)

---

# Scenario 2 — Wrong Default Gateway

## Problem

ADMIN-PC could not reach remote VLANs because of an incorrect default gateway configuration.

## Troubleshooting Process

- Ping testing
- Endpoint verification using `ipconfig`
- Gateway validation

## Root Cause

ADMIN-PC was configured with an incorrect default gateway address.

## Resolution

The correct default gateway was configured on the endpoint.

### Screenshots

![Ping Failure](s2-ping-failure.png)

![IP Configuration](s2-ipconfig.png)

![Gateway Fixed](s2-gateway-fixed.png)

![Connectivity Restored](s2-connectivity-restored.png)

---

# Scenario 3 — Wrong VLAN Assignment

## Problem

PC1 could not communicate on the network because the switch port was assigned to the wrong VLAN.

## Troubleshooting Process

- Endpoint verification
- VLAN verification
- Switchport analysis

## Root Cause

FastEthernet0/1 on SW2-Users was assigned to the incorrect VLAN.

## Resolution

The switchport was reassigned to VLAN 10.

### Screenshots

![Endpoint Troubleshooting](s3-endpoint-troubleshooting.png)

![VLAN Mismatch](s3-vlan-mismatch.png)

![VLAN Fix](s3-vlan-fix.png)

![Connectivity Restored](s3-connectivity-restored.png)

---

# Scenario 4 — Syslog Failure Caused by Trunk Misconfiguration

## Problem

SW2 syslog events failed to reach the centralized monitoring server because VLAN 20 was removed from the trunk link.

## Troubleshooting Process

- Syslog event generation
- Monitoring verification
- Trunk analysis
- VLAN transport verification

## Root Cause

VLAN 20 was missing from the trunk link between SW1-Core and SW3-Servers.

## Resolution

VLAN 20 was restored to the trunk allowed VLAN list.

### Screenshots

![Trunk Misconfiguration](s4-trunk-misconfiguration.png)

![SW2 Log Generation](s4-sw2-log-generation.png)

![Syslog Failure](s4-syslog-failure.png)

![Trunk Troubleshooting](s4-trunk-troubleshooting.png)

![Trunk Fix](s4-trunk-fix.png)

![Monitoring Restored](s4-monitoring-restored.png)

---

# Scenario 5 — ACL Blocking ICMP Traffic

## Problem

Management VLAN devices could not ping the Users VLAN because of an incorrectly applied ACL.

## Troubleshooting Process

- Connectivity verification
- ACL inspection
- ACL hit counter analysis
- Interface ACL verification

## Root Cause

An inbound ACL applied to VLAN 30 blocked ICMP traffic between VLANs.

## Resolution

The incorrect ACL was removed from the interface and deleted.

### Screenshots

![Normal Connectivity](s5-normal-connectivity.png)

![ACL Configuration](s5-acl-configuration.png)

![Ping Blocked](s5-ping-blocked.png)

![ACL Troubleshooting](s5-acl-troubleshooting.png)

![ACL Fix](s5-acl-fix.png)

![Connectivity Restored](s5-connectivity-restored.png)

---

## Skills Demonstrated

- Enterprise network troubleshooting
- Operational monitoring
- Syslog analysis
- Layer 2 troubleshooting
- Layer 3 troubleshooting
- VLAN troubleshooting
- ACL troubleshooting
- Fault isolation
- Inter-VLAN routing
- CLI-based diagnostics
- Structured troubleshooting methodology

---

## Author

Koray Erek
