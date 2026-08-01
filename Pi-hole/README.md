# Pi-hole

---

## Objective 

Deploy a network wide DNS filtering solution to block advertisements and tracking domains while gaining visibility into DNS traffic across devices on my home network.

---

## Why I chose Pi-hole

I wanted to learn more about DNS while improving privacy and reducing unwanted advertisement. Pi-hole acts as a DNS sinkhole, allowing DNS request to be filtered before devices connect to known advertising and tracking domains.

## What I learned 

- How DNS resolution works
- How clients communicate with DNS servers.
- The role of upstream DNS providers such as Cloudflare
- How Docker publishes container ports to the host
- How DNS filtering differes from browser based ad blocking
- The difference between a service being reachable and a service accepting request
- The security implications of exposing DNS services to the public internet

---

## Pi-hole Not Resolving DNS Requests

After configuring client devices to use Pi-hole as their DNS server, website failed to load.

<img width="1062" height="52" alt="Screenshot 2026-07-31 210413" src="https://github.com/user-attachments/assets/cc0b733d-d993-4309-b18f-d3b270665090" />

Pi-hole was receiving DNS requests but rejecting them due to its DNS listening configurations.

The issue was resolved by updating the Pi-hole configuration to allow DNS request from LAN clients and recreating the container.

---

### DNS vs Browser Ad Blocking

While testing Pi-hole, I learned that browser extensions such as uBlock Origin can block requests before DNS resolution occurs. This demonstrated how DNS filtering and browser based content filtering complement each other.

---

## Services and Ports

| Service | Port |
|----------|----------|
| DNS | 53 TCP/UDP |
| Web Interface | 80 |

---

## Outcome

Successfully deployed Pi-hole in a Docker container and configured both Windows and iPhone clients to use it as their DNS server. Verified functionality through query logs, dashboard statistics, and successful DNS resolution testing.

---

## Key Takeaway

Before this project, I barely knew what DNS was, despite it being a critical component of nearly every internet service. Troubleshooting Pi-hole helped me understand how clients locate services on the internet and how a DNS server can be reachable while still refusing client requests due to configuration issues.

---

## Screenshots

<img width="2560" height="1392" alt="image" src="https://github.com/user-attachments/assets/0ae791f1-f418-483b-91fb-02d8996daa31" />

<img width="2560" height="1392" alt="image" src="https://github.com/user-attachments/assets/fe3db50e-a3c8-4500-9c7e-82fbe967154f" />




