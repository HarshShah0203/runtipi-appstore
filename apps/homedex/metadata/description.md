# Homedex

**The missing inventory for your homelab.** Homedex builds a searchable record of the services, hosts, ports, routes, certificates, domains and changes your infrastructure reports, instead of another spreadsheet to maintain.

- **Docker**: containers, images, Compose stacks, ports and networks, read through the bundled socket proxy that rejects every write.
- **Proxmox VE and Tailscale**: nodes, VMs, containers and tailnet devices, each shown on the machine it runs on.
- **Reverse proxies**: Traefik, Caddy, Nginx Proxy Manager and nginx routes, followed from domain to container, with broken chains flagged.
- **Expiry and changes**: certificates and domains by days remaining, image updates, and what moved between scans.

Homedex only reads. It never starts, stops or reconfigures anything, and it sends no telemetry.

## First start

1. Fill in the **Admin password** (12 or more characters) in the install form. Homedex stores only its Argon2id hash on the first start and ignores the value once an admin exists, so the setup page is never open to whoever reaches it first.
2. Open Homedex and sign in with that password.
3. Add the first source: keep the prefilled Docker endpoint `tcp://docker-socket-proxy:2375`. That is the read-only socket proxy installed with this app. It allows GET on containers, images, networks, info and version, refuses every write (`POST=0`), publishes no port, and sits only on this app's own network, not on the shared Runtipi network.

Turn on **HTTPS only** only when you always open Homedex through an HTTPS domain.

## Links

- Source and documentation: https://github.com/HarshShah0203/homedex
- Connector guide: https://github.com/HarshShah0203/homedex/blob/main/docs/CONNECTORS.md
- Live demo with fabricated data: https://harshshah0203.github.io/homedex/
- Issues: https://github.com/HarshShah0203/homedex/issues
