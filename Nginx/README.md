# Nginx Proxy Manager 

## Objective 

Implement internal DNS and reverse proxy services to replace IP addresses and port numbers with user friendly hostnames for home lab services 

## Why I Chose This Project

As I added more services to my homelab, accessing each application through an IP address and port number became increasingly difficult to manage.

I implemented Pi-hole for internal DNS resolution and Nginx Proxy Manager as a centralized reverse proxy. This allowed services to be accessed through hostnames such as kuma.home and proxmox.home while also giving me hands-on experience with DNS, reverse proxying, HTTP/HTTPS, and TLS certificates.

## What I learned

- Configured Pi-hole local DNS records to resolve internal .home hostnames to the Nginx Proxy Manager server.
- Configured Nginx Proxy Manager reverse proxy hosts to forward requests to applications running on different ports and IP addresses.
- Learned how the HTTP Host header allows Nginx to route multiple domain names through the same server IP address.
- Configured Docker port mappings to expose Nginx Proxy Manager on standard HTTP and HTTPS ports 80 and 443.
- Learned the difference between a client-facing port and backend service port, such as Nginx accepting HTTPS on 443 while forwarding the request to Proxmox on 8006.
- Generated and deployed a self-signed TLS certificate for proxmox.home to provide HTTPS access to the Proxmox web interface.
- Learned how DNS, reverse proxying, and TLS work together to provide hostname-based access to internal applications.
- Used nslookup, curl, and Docker/Nginx logs to isolate problems between DNS resolution, Nginx host matching, HTTPS, and backend connectivity.

## Challenges 

### DNS and Reverse Proxy Routing 

Internal DNS records needed to resolve service hostnames to the Nginx Proxy Manager server rather than directly to each backend application.

This allowed Nginx to receive the request, inspect the requested hostname, and determine which backend service should receive the traffic.

### Proxmox Reverse Proxy

Proxmox required additional configuration because its web interface normally operates over HTTPS on port 8006.

During configuration, I encountered authentication errors, incorrect HTTP/HTTPS behavior, and requests reaching the Nginx Proxy Manager default site instead of the configured Proxmox proxy host.

I troubleshot the request path individually: DNS -> Nginx -> TLS/HTTPS -> Proxmox

### Validating DNS 

I used nslookup to confirm that proxmox.home resolved to the Nginx proxy Manager server which was 192.168.86.127, rather than directly to the proxmox host.

### Validating Nginx Routing

I used curl with a custom Host header to test Nginx independently of normal DNS resolution: curl -I -H "Host: proxmox.home" http://127.0.0.1

The resulting 301 Moved Permanently response redirecting to https://proxmox.home/ confirmed that Nginx recognized the hostname and that HTTPS redirection was functioning.

### TLS Configuration

Nginx Proxy Manager was changed to expose standard HTTPS port 443, and I generated a self-signed TLS certificate containing proxmox.home as the certificate hostname.

## Outcome 

Successfully implemented internal DNS and reverse proxying for multiple homelab applications.

Services that previously required addresses such as:

- 192.168.86.127:3001
- 192.168.86.127:8081
- 192.168.86.127:9443
- 192.168.86.118:8006

can now be accessed using:

- http://kuma.home
- http://pihole.home
- http://portainer.home
- https://proxmox.home

The project gave me practical experience troubleshooting an application request across multiple layers rather than treating DNS, HTTP, TLS, and reverse proxying as isolated concepts.

## Screenshots
