# Proxmox Home Lab Setup

Ez a dokumentum leírja a saját **Proxmox alapú home lab** telepítési és konfigurációs lépéseimet.  
A cél: otthoni környezetben többféle szolgáltatás (LXC, VM, Docker, Pi-hole, VPN, stb.) futtatása, tanulási és kísérletezési célokra.

---

## 1. Hardver környezet

- **Gép**: Dell Optiplex 5060
- **CPU**: Intel i5-8400
- **RAM**: 24 GB
- **Tárolás**: 256 GB SSD 2TB HDD
- **Hálózat**: 1 Gbit LAN

---

## 2. Telepítés

1. [Proxmox VE ISO](https://www.proxmox.com/en/downloads) letöltése.
2. Rufus / balenaEtcher segítségével bootolható USB készítése.
3. BIOS-ban:
   - Virtualization engedélyezése (Intel VT-x/AMD-V).
   - Boot sorrend USB-re állítása.
4. Telepítés után:
   - IP-cím kiosztása (statikus beállítás ajánlott).
   - Web UI elérhetősége: `https://192.168.1.220:8006`.

---

## 3. Alap konfiguráció

- Frissítés:
  ```bash
  apt update && apt full-upgrade -y
