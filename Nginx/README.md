# Nginx Proxy Manager 

## Objective 

Implement internal DNS and reverse proxy services to replace IP addresses and port numbers with user friendly hostnames for home lab services 

## Why I Chose This Project

As I added more services to my homelab, accessing each application through an IP address and port number became increasingly difficult to manage.

I implemented Pi-hole for internal DNS resolution and Nginx Proxy Manager as a centralized reverse proxy. This allowed services to be accessed through hostnames such as kuma.home and proxmox.home while also giving me hands-on experience with DNS, reverse proxying, HTTP/HTTPS, and TLS certificates.

## What I learned

[ ] Configured Pi-hole local DNS records to resolve internal .home hostnames to the Nginx Proxy Manager server.
[ ] Configured Nginx Proxy Manager reverse proxy hosts to forward requests to applications running on different ports and IP addresses.
Learned how the HTTP Host header allows Nginx to route multiple domain names through the same server IP address.
Configured Docker port mappings to expose Nginx Proxy Manager on standard HTTP and HTTPS ports 80 and 443.
Learned the difference between a client-facing port and backend service port, such as Nginx accepting HTTPS on 443 while forwarding the request to Proxmox on 8006.
Generated and deployed a self-signed TLS certificate for proxmox.home to provide HTTPS access to the Proxmox web interface.
Learned how DNS, reverse proxying, and TLS work together to provide hostname-based access to internal applications.
Used nslookup, curl, and Docker/Nginx logs to isolate problems between DNS resolution, Nginx host matching, HTTPS, and backend connectivity.
