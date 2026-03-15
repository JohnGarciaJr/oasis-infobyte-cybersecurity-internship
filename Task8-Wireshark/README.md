# Wireshark Network Traffic Capture

## Overview
This task involves capturing and analyzing network traffic using Wireshark. The goal was to observe HTTP traffic, inspect packet details, and understand how data flows across a network.

## Tools Used
- Wireshark
- Npcap (for packet capturing)

## Steps Performed
1. Installed Wireshark and Npcap.
2. Selected the active network interface and began capturing packets.
3. Generated HTTP traffic by visiting example websites.
4. Applied the filter `http` to isolate HTTP packets.
5. Analyzed GET and POST requests, TCP handshakes, and response codes.
6. Saved the capture as `wireshark_capture.pcap`.

## Key Observations
- HTTP traffic is unencrypted, allowing visibility into headers.
- GET requests showed the requested resource and host information.
- TCP handshake packets (SYN, SYN/ACK, ACK) were visible before HTTP communication.
- Response codes such as `200 OK` confirmed successful communication.

## Files Included
- `wireshark_capture.pcap` — Raw packet capture file.
