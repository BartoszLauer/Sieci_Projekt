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


## 📑 Spis treści
- [ Naprawa R2 + Router-on-a-Stick](CHANGES.md#-naprawa-r2--router-on-a-stick)
- [ Trunk na SW3](CHANGES.md#trunk-na-sw3)
- [Polecenie 4 — CDP / LLDP](CHANGES.md#polecenie-4-wyłącz-w-sieci-protokół-cdp-uruchom-protokół-lldp-i-wyłącz-go-tam-gdzie-jest-to-konieczne)
- [Polecenie 5 — RSTP + PortFast](CHANGES.md#polecenie-5--uruchom-w-istniejącej-sieci-rstp-w-miejscach-gdzie-jest-to-konieczne-uruchom-portfast)
- [Polecenie 6 — Zabezpieczenia](CHANGES.md#polecenie-6--zabezpiecz-wszystkie-urządzenia-sieciowe-i-wprowadź-baner-modt--nieautoryzowany-dostępzabroniony)
- [Polecenie 7 — Port Security](CHANGES.md#polecenie-7--na-przełączniku-sw1-sw2-uruchom-port-security-nieużywane-interfejsy-zabezpiecz-nawszystkich-przełącznikach)
- [Polecenie 8 — VTP](CHANGES.md#polecenie-8--ustaw-konfigurację-vtp-dla-sw1--server-sw2-i-sw3---client-podaj-dowolną-nazwę-domenyi-hasło-przypisz-interfejsy-przełączników-do-odpowiednich-sieci-vlan-ustaw-vlan-99-jako-natywny)
- [Polecenie 9 - i ](CHANGES.MD#)


