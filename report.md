# Wireshark Network Traffic Analysis Report

## Objective
Capture live network packets using Wireshark and identify basic protocols and traffic types.

## Tools
- Wireshark (version X.X)
- Browser and ping command to generate traffic

## Steps Performed
1. Installed Wireshark and selected the active network interface.
2. Started packet capture and generated traffic by browsing a website and pinging a server.
3. Stopped capture after ~1 minute.
4. Applied filters (`tcp`, `http`, `dns`, `tls`, `udp`) to isolate protocols.
5. Exported capture as `.pcap`.
6. Documented findings with screenshots and protocol summary.

---

## Protocols Identified
- **TCP**: Reliable transport protocol used for HTTP and TLS handshakes.
- **HTTP**: Unencrypted web traffic (GET requests and responses).
- **DNS**: Domain name resolution queries.
- **TLSv1.2**: Secure handshake for HTTPS connections.
- **QUIC**: Modern transport protocol over UDP, used by Google services.
- **UDP**: Lightweight transport protocol used by DNS and QUIC.

---

## Protocol Summary Table

| Protocol   | Purpose                          | Example Packet Info                                      | Notes                                      |
|------------|----------------------------------|-----------------------------------------------------------|--------------------------------------------|
| TCP        | Reliable transport layer         | SYN, SYN-ACK, ACK between 192.168.0.48 and 192.168.0.1    | Used for HTTP and TLS handshakes           |
| HTTP       | Web traffic (unencrypted)        | GET / HTTP/1.1 → 200 OK                                   | Shows basic browsing activity              |
| DNS        | Domain name resolution           | Query for example.com to 8.8.8.8                          | Uses UDP, resolves hostnames               |
| TLSv1.2    | Secure connection setup          | Client Hello, Server Certificate                          | Encrypts HTTPS traffic                     |
| QUIC       | Modern transport over UDP        | Initial QUIC packet to Google IP                         | Faster, secure alternative to TCP+TLS      |
| UDP        | Lightweight transport layer      | DNS and QUIC packets                                     | No handshake, used for speed               |

---

## Sample Packet Details
- **TCP Handshake**:
  - SYN from 192.168.0.48 → 192.168.0.1 (port 80)
  - SYN-ACK from 192.168.0.1 → 192.168.0.48
  - ACK from 192.168.0.48 → 192.168.0.1
- **HTTP Request**:
  - `GET / HTTP/1.1` from client
  - Response: `HTTP/1.1 200 OK (text/html)`
- **DNS Query**:
  - Query for `example.com` sent to 8.8.8.8
- **TLS Handshake**:
  - Client Hello and Server Certificate exchange
- **QUIC Traffic**:
  - UDP packets to Google IP (142.250.x.x) with QUIC stream data

---

## Screenshots
- `screenshots/handshake-http.png`: TCP three-way handshake and HTTP GET/200 OK.
- `screenshots/multi-protocol-capture.png`: Mixed traffic including TCP, UDP, DNS, TLS, and QUIC.

---

## Deliverables
- `capture.pcap`: Raw packet capture file.
- `report.md`: This analysis report.
- `screenshots/`: Supporting visuals.

---

## Conclusion
This lab demonstrates how Wireshark can be used to capture and analyze real-world traffic. The capture shows both encrypted (TLS, QUIC) and unencrypted (HTTP, DNS) protocols, highlighting the diversity of modern network communication. This structured analysis is useful for interview preparation, portfolio documentation, and hands-on learning in IT security and system administration.
