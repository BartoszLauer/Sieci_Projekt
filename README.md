## Dokumentacja Prac Projektu Sieci LAN

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
**Na przełączniku SW1, SW2 uruchom Port Security. Nieużywane interfejsy zabezpiecz na wszystkich przełącznikach.**

```
Urządzenie(config)# interface range (nieuzywane)
Urządzenie(config-if-range)# switchport mode access
Urządzenie(config-if-range)# switchport port-security
Urządzenie(config-if-range)# switchport port-security maximum 1
Urządzenie(config-if-range)# switchport port-security violation shutdown
Urządzenie(config-if-range)# switchport port-security mac-address sticky
```
