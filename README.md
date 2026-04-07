## Dokumentacja Prac Projektu Sieci LAN

| Urządzenie | Interfejs | Adres IP | Maska | Brama domyślna | Opis / VLAN |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R1 (DHCP)** | Gig 0/0 | 192.168.10.5 | 255.255.255.252 | - | Połączenie z R3 (Gig 0/1) |
| | Gig 0/1 | 192.168.10.2 | 255.255.255.252 | - | Połączenie z R2 (Gig 0/1) |
| **R2** | Gig 0/0.10 | 172.16.10.1 | 255.255.255.0 | - | Brama VLAN 10 |
| | Gig 0/0.20 | 172.16.20.1 | 255.255.255.0 | - | Brama VLAN 20 |
| | Gig 0/0.30 | 172.16.30.1 | 255.255.255.0 | - | Brama VLAN 30 |
| | Gig 0/1 | 192.168.10.1 | 255.255.255.252 | - | Połączenie z R1 (Gig 0/1) |
| | Gig 0/2 | 192.168.10.9 | 255.255.255.252 | - | Połączenie z R3 (Gig 0/2) |
| **R3 (NAT)** | Gig 0/0 | 200.100.1.1 | 255.255.255.0 | - | Połączenie z INTERNET |
| | Gig 0/1 | 192.168.10.6 | 255.255.255.252 | - | Połączenie z R1 (Gig 0/0) |
| | Gig 0/2 | 192.168.10.10 | 255.255.255.252 | - | Połączenie z R2 (Gig 0/2) |
| **INTERNET**| Gig 0/1 | 200.100.1.2 | 255.255.255.0 | - | Link do R3 |
| | Lo0 | 4.3.2.1 | 255.0.0.0 | - | Loopback (Cel testowy) |
| **PCA** | Fa 0 | 172.16.10.10 | 255.255.255.0 | 172.16.10.1 | VLAN 10 |
| **PCB** | Fa 0 | 172.16.20.10 | 255.255.255.0 | 172.16.20.1 | VLAN 20 |
| **PCC** | Fa 0 | 172.16.30.10 | 255.255.255.0 | 172.16.30.1 | VLAN 30 |
| **PCD** | Fa 0 | 172.16.10.11 | 255.255.255.0 | 172.16.10.1 | VLAN 10 |
| **PCE** | Fa 0 | 172.16.20.11 | 255.255.255.0 | 172.16.20.1 | VLAN 20 |
| **PCF** | Fa 0 | 172.16.30.11 | 255.255.255.0 | 172.16.30.1 | VLAN 30 |

### 🔹 Polecenie 4  
**Wyłącz w sieci protokół CDP. Uruchom protokół LLDP i wyłącz go tam, gdzie jest to konieczne.**

Konfigurację należy wykonać na przełącznikach **SW1** oraz **SW2**  
(SW3 – chyba nie trzeba nie wiem jak routery nie pamietam jak mowil kowalski).

#### 🔧 Konfiguracja:
```
Urządzenie(config)# no cdp run
Urządzenie(config)# lldp run
Urządzenie(config)# interface range f0/1-3
Urządzenie(config-if-range)# no lldp transmit
Urządzenie(config-if-range)# no lldp receive
```

### 🔹 Polecenie 5
**Uruchom w istniejącej sieci RSTP. W miejscach gdzie jest to konieczne uruchom PortFast.**

Konfigurację należy wykonać na przełącznikach SW1 oraz SW2.

#### 🔧 Konfiguracja:

Przykład:

```
Urządzenie(config)# spanning-tree mode rapid-pvst
i na portach
Urządzenie(config)# interface range f0/1-3 (porty trzeba dostosowac w zaleznosci od switcha)
Urządzenie(config-if-range)# spanning-tree portfast
```

### 🔹 Polecenie 6
**Zabezpiecz wszystkie urządzenia sieciowe i wprowadź baner MODT : Nieautoryzowany dostęp zabroniony**

```
Urządzenie(config)# enable secret [haslo]
Urządzenie(config)# line con 0
Urządzenie(config-line)# password [haslo]
Urządzenie(config-line)# login
Urządzenie(config)# banner motd "Nieautoryzowany dostep"
```
### 🔹 Polecenie 7
???
