# Dokumentace projektu LAN – Cisco Packet Tracer

### Autor: Filip Krejčí
### Projekt: Model lokální sítě s DHCP, DNS a Web službami.

Soubor projektu: lan.pkt
# 1. Zadání a cíle

Cílem úlohy bylo vytvořit funkční model LAN v simulátoru Cisco Packet Tracer. Síť obsahuje dva switche (S1, S2), dva koncové počítače (PC1, PC2), dva servery (SRV1, SRV2) a laptop pro správu.

  - S1: Připojení koncových stanic PC1 a PC2.

  - S2: Připojení serverů SRV1 a SRV2.

  - Služby: Konfigurace DHCP, DNS a HTTP (Web server).

  - Správa: Základní nastavení switchů přes konzolový kabel z Laptopu.

<img width="695" height="367" alt="obrazek" src="https://github.com/user-attachments/assets/ba8111f7-af8f-470d-ad0a-cbd58f5dcd3d" />


# 2. Výpočet síťového rozsahu (X)

Podle zadání byl rozsah sítě určen součtem ordinálních (ASCII) hodnot písmen příjmení (KREJCI) modulo 256.

Písmeno | ASCII hodnota

### Detailní výpočet hodnoty X (Příjmení: KREJCI)

| Písmeno | Ordinální hodnota (ASCII) |
| :---: | :---: |
| **K** | 75 |
| **R** | 82 |
| **E** | 69 |
| **J** | 74 |
| **C** | 67 |
| **I** | 73 |
| **CELKEM** | **440** |

Výpočet: $440 \pmod{256} = 184$

Výsledné X: 184

Přidělený síťový rozsah: 192.168.184.0 / 24

# 3. Adresní plán

| Zařízení | Rozhraní | IP adresa | Typ nastavení | Role v síti |
| :--- | :--- | :--- | :--- | :--- |
| **SRV1** | FastEthernet0 | 192.168.184.10 | Statická | DHCP + DNS Server |
| **SRV2** | FastEthernet0 | 192.168.184.20 | Statická | Web Server (HTTP) |
| **PC1** | FastEthernet0 | 192.168.184.30 | Statická | Koncová stanice |
| **PC2** | FastEthernet0 | 192.168.184.100+ | DHCP | Koncová stanice |
| **S1** | VLAN 1 | 192.168.184.2 | Management | Přístupový switch |
| **S2** | VLAN 1 | 192.168.184.3 | Management | Serverový switch |

# 4. Konfigurace služeb
DHCP (SRV1)

Server dynamicky přiděluje adresy koncovým zařízením v rozsahu 192.168.184.100 a výše.

<img width="640" height="411" alt="obrazek" src="https://github.com/user-attachments/assets/f6bbb9d2-237a-40f9-a060-d26a01b2be68" />

-------------------------------------------------
DNS (SRV1)

<img width="635" height="251" alt="obrazek" src="https://github.com/user-attachments/assets/703b9f0f-e932-48d7-9afd-3934097d3e9a" />

-------------------------------------------------
Web Server (SRV2)

Služba HTTP je aktivní. Soubor index.html byl upraven tak, aby zobrazoval toto

<img width="691" height="219" alt="obrazek" src="https://github.com/user-attachments/assets/fc48cd4a-75c9-4bcd-b604-d477c6a73826" />

-------------------------------------------------

# 5. Základní nastavení switchů

Konfigurace proběhla přes Laptop připojený konzolovým kabelem (port RS-232 -> Console).

Nastaven unikátní hostname (S1, S2).

Zabezpečení linky konzole heslem.

<img width="440" height="262" alt="obrazek" src="https://github.com/user-attachments/assets/66b335b6-a531-40fe-84de-a9fd8ec2c14e" />
<br><br>
<img width="432" height="247" alt="obrazek" src="https://github.com/user-attachments/assets/73755f25-001e-4e42-94cd-e2299537871f" />

# 6. Ověření funkčnosti (Screenshoty)

## PC1 – ipconfig
<img width="688" height="504" alt="obrazek" src="https://github.com/user-attachments/assets/58cf962f-6efd-42a5-862d-c4b77c79e452" />


## PC1 – ping na SRV2
<img width="397" height="402" alt="obrazek" src="https://github.com/user-attachments/assets/592747f5-902c-47ce-8100-94879bf51f9a" />
