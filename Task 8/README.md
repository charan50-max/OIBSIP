# Wireshark Network Traffic Capture and Analysis

## Objective

The goal of this task is to capture live network traffic using Wireshark, analyze HTTP packets, and understand how data flows between a client and a server over a network.

---

## Tools Used

Wireshark 4.6.2  
Npcap for packet capturing  
Windows 11  

---

## Capture Process

1. Installed Wireshark and Npcap on the system.
2. Selected the active Wi-Fi network interface.
3. Started live packet capture.
4. Generated traffic by visiting:
   - http://example.com
   - http://neverssl.com
   - Other regular websites.
5. Captured traffic for approximately one minute.
6. Stopped capture and saved the file as `wireshark_capture.pcap`.

---

## HTTP Traffic Filtering

To analyze HTTP traffic, the following display filter was used:

http

This filter displays only packets that belong to the HTTP protocol.

---

## Packet Analysis

From the filtered packets, the following information was observed:

### Example HTTP Request

- Source IP: 192.168.0.105  
- Destination IP: 104.18.26.120  
- Protocol: HTTP  
- Method: GET  
- Version: HTTP/1.1  

This shows the client requesting a web page from the server.

### Example HTTP Response

- Source IP: 104.18.26.120  
- Destination IP: 192.168.0.105  
- Status Code: 200 OK  
- Content Type: text/html  
- Transfer Encoding: chunked  

This indicates the server successfully responded to the client with the requested webpage.

---

## What This Demonstrates

This capture demonstrates:
- How HTTP requests and responses are transmitted.
- How data travels between a client and server.
- How unencrypted HTTP traffic can be inspected using packet analysis tools.

---

## Learning Outcome

This task helped in understanding:
- Live packet capturing
- Network protocol analysis
- Structure of HTTP communication
- Importance of encryption and secure communication

---


