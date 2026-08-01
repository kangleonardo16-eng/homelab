# Uptime Kuma

---

## Objective

Deploy a self hosted monitoring system solution to track the availability and response times of services running in my home lab.

---

## Why I chose Uptime Kuma

I wanted a simple way to monitor my services and be notified if they became unavailable. Uptime Kuma provides a web dashboard that can monitor websites, servers, containers, APIs, and network services while displaying uptime statistics and response times. 

---

## What I learned 

- How monitoring systems verify service availability 
- The Difference between host monitoring and service monitoring
- How to monitor services using Ping, TCP Port, HTTP(s), and DNS checks.
- How uptime response time metrics can be used to identify outages and performance issues
- How docker containers can be used to deploy monitoring solutions

---

## Monitors Configured

| Monitor | Type |
|---------|----------|
| Ubuntu Server | TCP Port (22) |
| Portainer | HTTP(s) |
| Pi-hole DNS | DNS |
| Pi-hole Web Interface | HTTP(s) |
| Uptime Kuma | HTTP(s) |

---

## Outcome

Successfully deployed Uptime Kuma in Docker and configured monitoring for multiple home lab services. The dashboard provides visibility into service availability and helps identify issues before they impact users.

---

## Screenshots

<img width="2560" height="1392" alt="image" src="https://github.com/user-attachments/assets/353420c4-27b1-40e6-a63b-9a5f6bc50b98" />
<img width="2560" height="1392" alt="image" src="https://github.com/user-attachments/assets/1ccadb61-e90a-46a7-b4c4-25c955cc4db5" />

