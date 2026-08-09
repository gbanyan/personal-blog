---
locale: en
translation_status: translated
translation_id: "posts/OPNsense 在 Proxmox VE 內安裝筆記"
title: OPNsense Virtualization Installation Notes on Proxmox VE
slug: opnsense-virtualization-in-proxmox-ve
ghost_id: 67e4d4f6c5a22a0001354611
type: post
status: published
visibility: public
featured: false
created_at: '2025-03-27T04:32:54.000Z'
updated_at: '2025-03-27T04:38:57.000Z'
published_at: '2023-01-29T10:46:00.000Z'
custom_excerpt: Replaced the soft router hardware and updated my notes accordingly.
tags:
- Linux
- Apps - 軟體
authors:
- Gbanyan
feature_image: ../assets/photo-1520869562399-e772f042f422.jpg
---

## Preface

* Replaced the soft router hardware and updated my notes accordingly.
* This post is a continuation of [Proxmox VE + PfSense 安裝](/blog/proxmox-ve-pfsense-installation-note).
  + The network installation architecture within Proxmox VE remains similar, utilizing the paravirtualized network interface controller (Virtio Net).
  + Testing showed that the Intel J4125 paired with the Intel i225v network card can achieve the full 300M / 100M speeds without configuring PCIe passthrough.
* The switch to OPNsense was made with the following considerations:
  + PfSense requires a subscription (PfSense Plus) for more aggressive updates. Although it's currently free for home users, future charges cannot be ruled out.
  + OPNsense has a more proactive update strategy and a shorter security update cycle.
  + Zenarmor and other third-party packages can be installed, though I ended up removing Zenarmor later on.
  + The OPNsense UI is more user-friendly, allowing quick navigation to desired settings via search.

## Installation

* Assign the Port vmbr0 to WAN and vmbr1 to LAN (Refer to the images in the PfSense notes)
* Skip the lagg and vlan configuration
* Default account and password for enter installation
  + account: installer
  + pass: opnsense
* VM settings in Proxmox VE
  + machine type: Q35
  + processors type: host
  + OS type: other
  + Adjust other CPU and memory settings according to needs.

## Configuration

### PPPoE settings with IPv6 (Applicable for Hinet)

* Fill out PPPoE info to establish connection
* Tick "Use IPv4 connectivity option"
* at LAN IPv6 section, IPv6 configuration type -> Track Interface, and the options below interface select "WAN"
* In the Firewall options, Tick "allow IPv6"
* Add IPv6 ICMP allow rule in WAN firewall rule
* If you want to use a self-hosted DNS (Adguard Home or Pi-Hole) and apply it to IPv6:
  + Tick the "Manual Router announcement management"
  + Fill the DNS IPv4 settings in the "Router announcement"
  + Hinet IPv6 is Stateless (Stateless DHCPv6 + SLAAC)
  + Disable the DHCPv6 service in the LAN
  + The logic here is that IPv6 DNS requests can simply be sent to the IPv4 address DNS server, which will still return IPv6 resolution addresses.

### Security

#### System

* Disable the listen service including WebUI, ssh, Unbound on WAN surface
* Install the CrowdSec, and enable Intrusion Detection
  + Disable hardware net acceleration related "Interfaces" > "Settings"
* Configure the SSH Key, disable the password login

#### Intrusion Detection (Suricata) (IPS/IDS)

* Download rule sets based on service used
* Rule set with using sites name (p2p, Facebook, Youtube) do not apply
* ET Pro rule set need suscription

#### Crowdesc

* Connected to the cloud database to detect the attackers IPs and block
* Collection for different scenarios (windows, nginx, ...)can only be added through shell command
* The hub for adding the scenario rule [Hub |](https://hub.crowdsec.net)

#### Firehol IP list subscription

* [FireHOL Block List ( Botnets, Attacks, Malware....)](https://forum.opnsense.org/index.php?topic=17596.0)
* Follow the guide to add alias of Firehol level 2
* Add the Cron tab to update the Firewall alias

#### VLAN Configuration (For creating a guest network or dedicated IoT network)

* Add VLAN, assign Tag, and make Proxmox VE vtnet aware vlan
* Assign DHCP server
* Add Firewall rule to make the VLAN network unable to access the LAN

#### GeoIP and Ailases for Firewall Block (If you want to block specific countries/regions)

* Register the Maxmind GeoIP database
* Follow the guide to add Firewall aliases
* Configure to block the specific countries

### Cron (Remember to set up updates for each list after security configuration)

* System and packages update
* Suricata blocklist update
* Firewall aliases updates (FireHol, GeoIP)

### Others Packages

* Netdata: Another monitoring service
* Wake-On-LAN: For waking up machines remotely
* UPNP: Use with caution if you have security concerns; used for punching holes for services within the LAN
* Tailscale [OPNsense安装配置Tailscale | 鐵血男兒的BLOG](https://pfschina.org/wp/?p=9163)
* Wireguard [How to Set Up WireGuard in OPNsense in 2023 - WunderTech](<https://www.wundertech.net/>
