# 🛠️ Aktulny Konfiguracja sieci (co zostalo zrobione)

**Trunk na SW3**

```bash
Switch(config)#interface Gig0/1
Switch(config-if)#switchport mode trunk
```

---

## Polecenie 4 Wyłącz w sieci protokół CDP. Uruchom protokół LLDP i wyłącz go tam gdzie jest to konieczne.

**CDP OFF / LLDP ON (wszystkie urządzenia)**

```bash
NazwaUrzadniea(config)#no cdp run
NazwaUrzadniea(config)#lldp run
```

---

**Wyłączenie LLDP na portach użytkowników**

**SW1**

```bash
SW1(config)#interface range fa0/1-4
SW1(config-if-range)#no lldp transmit 
SW1(config-if-range)#no lldp receive
```

**SW2**

```bash
SW2(config)#interface range fa0/1-3
SW2(config-if-range)#no lldp transmit 
SW2(config-if-range)#no lldp receive
```

**R3**

```bash
R3(config)#interface gig0/1
R3(config-if)#no lldp transmit 
R3(config-if)#no lldp receive 
```

---

## Polecenie 5 — Uruchom w istniejącej sieci RSTP. W miejscach gdzie jest to konieczne uruchom PortFast

**Włączenie RSTP**

```bash
(config)#spanning-tree mode rapid-pvst 
```

**PortFast (porty dostępowe)**

**SW1**

```bash
SW1(config)#interface range fa0/1-4
SW1(config-if-range)#spanning-tree portfast
```

**SW2**

```bash
SW2(config)#interface range fa0/1-3
SW2(config-if-range)#spanning-tree portfast 
```

---

## Polecenie 6 — Zabezpiecz wszystkie urządzenia sieciowe i wprowadź baner MODT : Nieautoryzowany dostępzabroniony

```bash
nic
```


## Polecenie 7 — Na przełączniku SW1, SW2 uruchom Port Security. Nieużywane interfejsy zabezpiecz nawszystkich przełącznikach.

**SW1**

```bash
SW1(config)#interface range fa0/1 - 4
SW1(config-if-range)#switchport mode access
SW1(config-if-range)#switchport port-security
SW1(config-if-range)#switchport port-security maximum 1
SW1(config-if-range)#switchport port-security violation restrict
SW1(config-if-range)#switchport port-security mac-address sticky

SW1(config)#interface range fa0/5 - 24
SW1(config-if-range)#shutdown
```

---

**SW2**

```bash
SW2(config)#interface range fa0/1 - 3
SW2(config-if-range)#switchport mode access
SW2(config-if-range)#switchport port-security
SW2(config-if-range)#switchport port-security maximum 1
SW2(config-if-range)#switchport port-security violation restrict
SW2(config-if-range)#switchport port-security mac-address sticky

SW2(config)#interface range fa0/4 - 24
SW2(config-if-range)#shutdown
```

---

## Polecenie 8 — Ustaw konfigurację VTP dla SW1 – server, SW2 i SW3 - client. Podaj dowolną nazwę domenyi hasło. Przypisz interfejsy przełączników do odpowiednich sieci VLAN. Ustaw VLAN 99 jako natywny.


**SW1 (SERVER)**

```bash
SW1(config)#vtp mode server
SW1(config)#vtp domain ajp.domain.pl
SW1(config)#vtp password cisco

SW1(config)#interface range gig0/1-2 
SW1(config-if-range)#switchport mode trunk 
SW1(config-if-range)#switchport trunk native vlan 99
```

---

**SW2 (CLIENT)**

```bash
SW2(config)#vtp mode client
SW2(config)#vtp domain ajp.domain.pl
SW2(config)#vtp password cisco

SW2(config)#interface range gig0/1-2 
SW2(config-if-range)#switchport mode trunk 
SW2(config-if-range)#switchport trunk native vlan 99
```

---

**SW3 (CLIENT)**

```bash
SW3(config)#vtp mode client
SW3(config)#vtp domain ajp.domain.pl
SW3(config)#vtp password cisco

SW3(config)#interface range gig0/1 - 2, fa0/1
SW3(config-if-range)#switchport mode trunk
SW3(config-if-range)#switchport trunk native vlan 99
```

---


## Polecenie 9 Zabezpiecz wszystkie linie VTY na przełącznikach i uruchom na urządzeniach możliwość zdalnego dostępu przez SSH.
**Na SW1, SW2, SW3, R1, R2, R3**
```bash
SW1(config)#ip domain-name ajp.domain.pl
SW1(config)#crypto key generate rsa (wpisujmey tutaj 1024)
SW1(config)#username admin secret admin
SW1(config)#line vty 0 15
SW1(config-line)#transport input ssh
SW1(config-line)#login local
SW1(config-line)#exit
SW1(config-line)#ip ssh version 2 
```

nie zrobilem jeszcze na routerach tylko na 3 switach (na routerach line vty 0 4)

## Polecenie 10

```bash
```

## Polecenie 11 - Na routerze podłączonym do przełącznika uruchom Inter VLAN Routing.

```bash
R2(config)#interface Gig0/0
R2(config-if)#no shutdown

R2(config)#interface Gig0/0.10
R2(config-subif)#encapsulation dot1Q 10
R2(config-subif)#ip address 172.16.10.1 255.255.255.0

R2(config)#interface Gig0/0.20
R2(config-subif)#encapsulation dot1Q 20
R2(config-subif)#ip address 172.16.20.1 255.255.255.0

R2(config)#interface Gig0/0.30
R2(config-subif)#encapsulation dot1Q 30
R2(config-subif)#ip address 172.16.30.1 255.255.255.0
```

## Polecenie 12

```bash
```

## Polecenie 13 - Na zaznaczonym w topologii sieci routerze (DHCP) uruchom serwer DHCP dla wszystkich sieci VLAN

**R1_DHCP**
```bash
R1_DHCP(config)#ip dhcp excluded-address 172.16.10.1
R1_DHCP(config)#ip dhcp excluded-address 172.16.20.1
R1_DHCP(config)#ip dhcp excluded-address 172.16.30.1

R1_DHCP(config)#ip dhcp pool VLAN10
R1_DHCP(dhcp-config)#network 172.16.10.0 255.255.255.0
R1_DHCP(dhcp-config)#default-router 172.16.10.1

R1_DHCP(config)#ip dhcp pool VLAN20
R1_DHCP(dhcp-config)# network 172.16.20.0 255.255.255.0
R1_DHCP(dhcp-config)# default-router 172.16.20.1


R1_DHCP(config)#ip dhcp pool VLAN30
R1_DHCP(dhcp-config)# network 172.16.30.0 255.255.255.0
R1_DHCP(dhcp-config)# default-router 172.16.30.1
```

## Polecenie 14

```bash
```

## Polecenie 15

```bash
```

## Polecenie 16

```bash
```

---


