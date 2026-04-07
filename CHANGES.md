# 🛠️ Konfiguracja sieci — krok po kroku

---

## 🔧 1. Naprawa R2 + Router-on-a-Stick

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

💡 *Router obsługuje wiele VLAN-ów przez jeden interfejs fizyczny.*

---

## 🔌 2. Trunk na SW3

```bash
Switch(config)#interface Gig0/1
Switch(config-if)#switchport mode trunk
```

---

# ⚙️ Polecenie 4 — Konfiguracja globalna

## 🌐 CDP OFF / LLDP ON (wszystkie urządzenia)

```bash
NazwaUrzadniea(config)#no cdp run
NazwaUrzadniea(config)#lldp run
```

---

## 🚫 Wyłączenie LLDP na portach użytkowników

### SW1

```bash
SW1(config)#interface range fa0/1-4
SW1(config-if-range)#no lldp transmit 
SW1(config-if-range)#no lldp receive
```

### SW2

```bash
SW2(config)#interface range fa0/1-3
SW2(config-if-range)#no lldp transmit 
SW2(config-if-range)#no lldp receive
```

### R3

```bash
R3(config)#interface gig0/1
R3(config-if)#no lldp transmit 
R3(config-if)#no lldp receive 
```

---

# 🌳 Polecenie 5 — RSTP + PortFast

## 🔁 Włączenie RSTP

```bash
(config)#spanning-tree mode rapid-pvst 
```

## ⚡ PortFast (porty dostępowe)

### SW1

```bash
SW1(config)#interface range fa0/1-4
SW1(config-if-range)#spanning-tree portfast
```

### SW2

```bash
SW2(config)#interface range fa0/1-3
SW2(config-if-range)#spanning-tree portfast 
```

---

# 🔐 Polecenie 6 — Zabezpieczenia + Baner

```bash
! TODO: konfiguracja zabezpieczeń + MOTD
```

📢 **Baner:**
`Nieautoryzowany dostęp zabroniony`

---

# 🔒 Polecenie 7 — Port Security

## SW1

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

## SW2

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

# 🧩 Polecenie 8 — VTP + VLAN + Trunk

## 🖥️ SW1 (SERVER)

```bash
SW1(config)#vtp mode server
SW1(config)#vtp domain ajp.domain.pl
SW1(config)#vtp password cisco

SW1(config)#interface range gig0/1-2 
SW1(config-if-range)#switchport mode trunk 
SW1(config-if-range)#switchport trunk native vlan 99
```

---

## 🖥️ SW2 (CLIENT)

```bash
SW2(config)#vtp mode client
SW2(config)#vtp domain ajp.domain.pl
SW2(config)#vtp password cisco

SW2(config)#interface range gig0/1-2 
SW2(config-if-range)#switchport mode trunk 
SW2(config-if-range)#switchport trunk native vlan 99
```

---

## 🖥️ SW3 (CLIENT)

```bash
SW3(config)#vtp mode client
SW3(config)#vtp domain ajp.domain.pl
SW3(config)#vtp password cisco

SW3(config)#interface range gig0/1 - 2, fa0/1
SW3(config-if-range)#switchport mode trunk
SW3(config-if-range)#switchport trunk native vlan 99
```

---

# 📌 Kolejne polecenia

## 📍 Polecenie 9

```bash
```

## 📍 Polecenie 10

```bash
```

## 📍 Polecenie 11

```bash
```

## 📍 Polecenie 12

```bash
```

## 📍 Polecenie 13

```bash
```

## 📍 Polecenie 14

```bash
```

## 📍 Polecenie 15

```bash
```

## 📍 Polecenie 16

```bash
```

---

# ✅ Status

✔ Router-on-a-Stick
✔ Trunki
✔ RSTP
✔ Port Security
✔ VTP

🚧 Do zrobienia: zabezpieczenia + reszta poleceń
