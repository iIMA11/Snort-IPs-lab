## Inline Intrusion Prevention System with Snort + Real-Time Dashboard

A two-subnet lab implementing Snort in inline (NFQUEUE) mode to actively 
detect and block SQL injection attacks (and some other rules for alert), 
with a Flask/Chart.js dashboard for real-time alert visualization.

## Overview
[2-3 sentences: what problem this solves, IDS vs IPS distinction, 
what makes this "inline" rather than passive]

## Architecture
- Kali (attacker) — Subnet A
- Snort IPS VM — bridges both subnets, inspects and drops malicious traffic
- Ubuntu Server (target) — Subnet B

## How it works
1. Snort runs in inline mode via NFQUEUE, receiving packets from iptables
2. Custom rules (SIDs 2001-2004) match SQL injection patterns
3. Matched packets are dropped before reaching the target
4. Alerts are parsed and pushed to a live Flask dashboard

## Dashboard
<img width="1837" height="906" alt="Screenshot 2026-08-26 222120" src="https://github.com/user-attachments/assets/ee5f2a24-60d2-47bd-a336-b7c2f79dc730" />
Real-time alert feed, protocol breakdown charts, live search and 
pagination, built with Flask + Chart.js.

## Demo
From the Snort IPS VM:
<img width="1328" height="260" alt="image" src="https://github.com/user-attachments/assets/a8535c79-2b8d-4909-81a8-43e1e27063f6" />

The client Kali VM:

<img width="552" height="238" alt="Screenshot 2026-08-29 163011" src="https://github.com/user-attachments/assets/0d6f6300-ea62-4b15-9acf-68f01d4c64ef" />

## Tech stack
Snort 2.9.x, NFQUEUE, libnetfilter-queue, Flask, Chart.js, VirtualBox
