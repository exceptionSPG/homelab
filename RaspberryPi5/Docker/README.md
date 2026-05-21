
# Docker services on my raspberry pi 5

Below are my currently configured docker services:
```
├── audiobookshelf
├── cloudflared
├── essentials
├── npm
├── openwebui_ollama
├── pi-hole
├── portainer
├── qbittorrent
├── siddhibuddhi-store
├── traefik
└── wpblog
``` 



## Shared Networks
We will create two-separate docker networks, one for external facing services, and others as internal services connecting to proxy. 


`docker network create proxy-network --driver bridge`
`docker network create proxy-out-network --driver bridge`



## Volumes mount
We will separate our compose file directory, with our local mounted volumes, to keep code and data separated. While, this may pose it's own pros/cons, we are considering this approach for better maintainability.

Create <container-name>/ inside dockerVolumes directory for each container requiring volume mount
