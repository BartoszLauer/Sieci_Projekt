## Tabela Adresacji

| Urządzenie | Interfejs | Adres IP | Maska | Brama domyślna | Opis / VLAN |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R1 (DHCP)** | Gig 0/0 | 192.168.10.5 | 255.255.255.252 | - | Połączenie z R3 |
| | Gig 0/1 | 192.168.10.2 | 255.255.255.252 | - | Połączenie z R2 |
| **R2** | **Gig 0/0.10** | 172.16.10.1 | 255.255.255.0 | - | Brama VLAN 10 |
| | **Gig 0/0.20** | 172.16.20.1 | 255.255.255.0 | - | Brama VLAN 20 |
| | **Gig 0/0.30** | 172.16.30.1 | 255.255.255.0 | - | Brama VLAN 30 |
| | **Gig 0/0.99** | **172.16.99.1** | **255.255.255.0**| - | **Brama Zarządzania** |
| | Gig 0/1 | 192.168.10.1 | 255.255.255.252 | - | Połączenie z R1 |
| | Gig 0/2 | 192.168.10.9 | 255.255.255.252 | - | Połączenie z R3 |
| **R3 (NAT)** | Gig 0/0 | 200.100.1.1 | 255.255.255.0 | - | Połączenie z INTERNET |
| | Gig 0/1 | 192.168.10.6 | 255.255.255.252 | - | Połączenie z R1 |
| | Gig 0/2 | 192.168.10.10 | 255.255.255.252 | - | Połączenie z R2 |
| **INTERNET**| Gig 0/1 | 200.100.1.2 | 255.255.255.0 | - | Link do R3 |
| | Lo0 | 4.3.2.1 | 255.0.0.0 | - | Cel testowy (Loopback) |
| **SW1** | **Vlan 99** | **172.16.99.11** | **255.255.255.0**| **172.16.99.1** | **Adres do SSH** |
| **SW2** | **Vlan 99** | **172.16.99.12** | **255.255.255.0**| **172.16.99.1** | **Adres do SSH** |
| **SW3** | **Vlan 99** | **172.16.99.13** | **255.255.255.0**| **172.16.99.1** | **Adres do SSH** |
| **PCA** | Fa 0 | 172.16.10.10 | 255.255.255.0 | 172.16.10.1 | VLAN 10 |
| **PCB** | Fa 0 | 172.16.20.10 | 255.255.255.0 | 172.16.20.1 | VLAN 20 |
| **PCC** | Fa 0 | 172.16.30.10 | 255.255.255.0 | 172.16.30.1 | VLAN 30 |
| **PCD** | Fa 0 | 172.16.10.11 | 255.255.255.0 | 172.16.10.1 | VLAN 10 |
| **PCE** | Fa 0 | 172.16.20.11 | 255.255.255.0 | 172.16.20.1 | VLAN 20 |
| **PCF** | Fa 0 | 172.16.30.11 | 255.255.255.0 | 172.16.30.1 | VLAN 30 |



## 📑 Polecenie i aktualny stan znajdziesz tutaj
- [Dokumentacja](CHANGES.md#polecenie-4-wyłącz-w-sieci-protokół-cdp-uruchom-protokół-lldp-i-wyłącz-go-tam-gdzie-jest-to-konieczne)



