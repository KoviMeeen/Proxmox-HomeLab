# Proxmox-HomeLab
My Proxmox home lab documentation and configurations

# Proxmox Home Lab

Ez a repository a saját **Proxmox home-lab** környezetem dokumentációját tartalmazza.  
A célom, hogy bemutassam a telepítési lépéseket, a konfigurációkat és a tanulási folyamatot.  

---

## 🖥 Hardver
- **Host**: Dell Optiplex 5060
- **CPU**: Intel i5-8400
- **RAM**: 24 GB
- **Storage**: 256 SSD + 2TB HDD

---

## ⚙️ Használt szoftverek
- **Hypervisor**: Proxmox VE 9.0.9
- **LXC-k**:
  - OpenVPN szerver (ubuntu 22.04.5)
  - Pi-hole DNS (Debian GNU/Linux 12 PiHol)
  - Transmission (ubuntu 22.04.5)
  - FileServer (turnkey-fileserver)
  - Plex (ubuntu 22.04.5)
 - **VM-ek**
  - Debian 13.0

---

## 📂 Dokumentáció
- [Proxmox setup](docs/proxmox-setup.md)
- [VM template-ek](docs/vm-templates.md)
- [Backup stratégia](docs/backups.md)
- [Monitoring](docs/monitoring.md)

---

## 🔌 Hálózati felépítés
A hálózat egyszerűsített ábrája (diagram a `docs/network-diagram.png` fájlban található):  

-Huawei HG8121H (ISP router)

LAN IP: 192.168.100.1/24
NAT-ol az internet felé
Port forwarding beállítva OpenVPN-hez

-TP-Link AX50 (belső hálózat)

WAN IP: pl. 192.168.100.1 a Huawei LAN-ján belül
LAN IP: 192.168.1.1/24
DHCP a belső hálóra
Port forwarding szintén OpenVPN-hez

-Proxmox host

IP a TP-Link LAN-on: 192.168.1.220:8006

-VM-ek / LXC-k

Címek a TP-Link 192.168.1.0/24 hálózatból

FileServer 		192.168.1.200/24
Plex			192.168.1.202/24
Torrent			192.168.1.201/24
PiHole			192.168.1.254/24
OpenVPN			192.168.1.250/24
Debian Desktop	DHCP

OpenVPN LXC: saját IP, port forwarding mindkét routeren

---

## 📌 Tervek
- Kubernetes cluster kiépítése  
- Terraformmal automatizált VM provisioning  
- CI/CD pipeline GitLab Runnerekkel  

---

## 🔑 Megjegyzés
Ez a projekt tanulási célból készült. Bárki használhatja inspirációként.

