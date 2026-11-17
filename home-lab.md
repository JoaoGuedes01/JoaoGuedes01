# Home Lab

> The short version of my homelab. The long version, with the reasoning, mistakes and screenshots, is a 5-part series on [joaoguedes.net](https://joaoguedes.net/blog).

It has been serving my self-hosted apps since 2022. It started as a free machine built from leftovers (the **Frankenlab**) and was rebuilt in 2026 into a single, quiet Proxmox host that I treat like a small production environment: least privilege, one login for everything, backups I actually verify, and alerts that reach my phone.

| Part | Read it |
|---|---|
| 1. The Frankenlab: a cost-free lab from hand-me-down parts | [joaoguedes.net/blog/the-frankenlab](https://joaoguedes.net/blog/the-frankenlab) |
| 2. The Rebuild: hardware, ZFS, LXC instead of VMs | [joaoguedes.net/blog/the-rebuild](https://joaoguedes.net/blog/the-rebuild) |
| 3. The Media Stack: Jellyfin, requests, the arr stack, music | [joaoguedes.net/blog/the-media-stack](https://joaoguedes.net/blog/the-media-stack) |
| 4. The Infrastructure: DNS, certificates, SSO, vault, VPN | [joaoguedes.net/blog/the-infrastructure](https://joaoguedes.net/blog/the-infrastructure) |
| 5. Keeping It Alive: backups, disk health, monitoring, updates | [joaoguedes.net/blog/keeping-it-alive](https://joaoguedes.net/blog/keeping-it-alive) |

---

## At a glance

| | |
|---|---|
| **Hypervisor** | Proxmox VE, ten LXC containers |
| **Compute** | Intel Core i7-8700K (6C/12T), 32 GB DDR4, Intel UHD 630 for transcoding. Reused from my old gaming rig |
| **Storage** | 1 TB NVMe for Proxmox and container disks, 2 × 8 TB ZFS mirror (`tank`) for data |
| **Network** | UniFi router, Pi-hole + Unbound for DNS, wildcard certificate behind a reverse proxy |
| **Identity** | Authentik (SSO + MFA in one place), Vaultwarden for passwords |
| **Remote access** | Tailscale subnet router and Teleport for me, Cloudflare Tunnel for the few things I share |
| **Backups** | Proxmox Backup Server on a second machine (the old Frankenlab), plus ZFS mirror and scrubs |
| **Monitoring** | Uptime Kuma, a host health script and heartbeats, all reporting to Discord |

---

## Architecture

```mermaid
flowchart TB
    internet["Internet"]
    cf["Cloudflare Tunnel<br/>(outbound only, no forwarded ports)"]
    me["Me, away from home"]

    subgraph home["Home network"]
        router["UniFi router<br/>Teleport VPN"]

        subgraph pve["Proxmox host (i7-8700K / 32 GB)"]
            direction TB
            subgraph net["Network & access"]
                dns["DNS<br/>Pi-hole + Unbound"]
                proxy["Reverse proxy<br/>wildcard TLS"]
                ts["Tailscale<br/>subnet router"]
                tunnel["Tunnel connector"]
            end
            subgraph apps["Apps"]
                mgmt["Docker: management<br/>Authentik, Vaultwarden, Uptime Kuma"]
                media["Docker: media automation"]
                music["Docker: music"]
                jelly["Jellyfin"]
                navi["Navidrome"]
            end
            samba["Samba + Cockpit<br/>file sharing"]
            zfs[("ZFS mirror 'tank'<br/>2 x 8 TB")]
            nvme[("NVMe<br/>container disks")]
        end

        pbs["Second machine<br/>Proxmox Backup Server"]
    end

    discord["Discord<br/>alerts"]

    internet --> cf --> tunnel --> proxy
    me --> ts --> router
    router --> dns
    proxy --> mgmt & media & music & jelly & navi
    media & music & jelly & navi & samba --> zfs
    apps --> nvme
    pve -->|"scheduled backups"| pbs
    mgmt -->|"checks + webhook"| discord
```

### What runs where

| Container | Role |
|---|---|
| DNS | Pi-hole with its own recursive resolver (Unbound), so ads are blocked and I don't depend on someone else's DNS |
| Reverse proxy | Clean names and a real wildcard certificate for every service |
| VPN | Tailscale subnet router that gets me back into the house |
| File sharing | Samba, managed through Cockpit, so every device sees the media as a network drive |
| Docker (management) | Authentik, Vaultwarden, Uptime Kuma and other admin apps |
| Docker (media automation) | Seerr, Radarr, Sonarr, Bazarr and friends |
| Docker (music) | Soulseek and music tooling |
| Jellyfin / Navidrome | Video and music servers |
| Tunnel | Cloudflare connector for the few services I share with family and friends |

---

## Design decisions

- **LXC over VMs.** Containers share the host kernel, start in seconds and cost almost no RAM. Ten of them use less than 15% of the machine. I harden what I can (unprivileged where possible) and accept the remaining privileged ones as a conscious trade-off.
- **ZFS owns the disks.** A mirror survives a dead drive, checksums catch silent corruption, and a monthly scrub repairs it. All media lives in one dataset so downloads can be *hardlinked* into the library instead of copied.
- **One identity.** Management apps sit behind Authentik, so MFA lives in one place and there is one off-switch.
- **Don't expose what you don't need.** Nothing listens on my home connection. Sensitive tools are LAN/VPN only, and only what other people really need is published through the tunnel.
- **Back up what is irreplaceable.** The whole lab is backed up at the Proxmox level, but I only back up *data* I can't get back (photos, home videos, configs). Media can be re-downloaded or re-ripped.
- **Boring monitoring.** No heavy stack. Uptime Kuma checks the services, a script checks the host, and heartbeats check that the monitoring itself is still alive.

---

## Security model

| Layer | Approach |
|---|---|
| **Ingress** | Cloudflare Tunnel (outbound connection), no inbound port forwarding |
| **Admin access** | Only from the LAN or over VPN (Tailscale / Teleport) |
| **Identity** | SSO + MFA through Authentik, passwords in self-hosted Vaultwarden |
| **Isolation** | One container per role, unprivileged where possible, same UID/GID only for services that share media |
| **Storage** | Bind-mount only the paths a service needs |
| **Recovery** | PBS backups, ZFS mirror and scrubs, SMART tests, all verified on a schedule |

### Threat model

| Threat | Vector | Mitigation |
|---|---|---|
| Unauthorized remote access | Exposed services | No forwarded ports, tunnel only for shared apps behind accounts, admin over VPN |
| Credential theft | Phished or reused password | Vaultwarden, unique passwords, MFA at the Authentik layer |
| Container breakout | Vulnerability in an app | Per-role containers, unprivileged where possible, scoped mounts |
| Vulnerable public app | Unpatched service behind the tunnel | Cloudflare proxy in front, prompt updates, share as little as possible |
| Data loss | Disk failure, bad update, ransomware, fire | ZFS mirror, scheduled PBS backups with verification; off-site copy is next |
| Silent failure | Alerts or monitoring stop working | Heartbeats that notify me when the monitoring itself goes quiet |

---

## What's next

- Off-site copy of the irreplaceable data, to complete the 3-2-1 rule
- Nightly instead of weekly backups
- Immich for photos (once the backups are sorted), Paperless-ngx, Mealie and Komga
- Karakeep or Linkwarden for saved links
- VLAN segmentation (IoT, management, media)
- OpenTelemetry pipeline for metrics, logs and traces
