# Sieci_Projekt

Polecenie 4 - Wyłącz w sieci protokół CDP. Uruchom protokół LLDP i wyłącz go tam gdzie jest to konieczne.

Trzeba to zrobic na urzadzeniach SW1 i SW2 (tego jestem pewien) (wydaje mi sie ze na SW3 NIE TRZEBA) a jezeli chodzi o routery to musze to przemyslec na ktore trzeba 
```
SW(config)# no cdp run
SW(config)# lldp run
SW(config)# interface range f0/1-3
SW(config-if-range)# no lldp transmit
SW(config-if-range)# no lldp receive
```
Polecenie 5 - Uruchom w istniejącej sieci RSTP. W miejscach gdzie jest to konieczne uruchom PortFast.

Na SW1 i SW2 
```
SW(config)# spanning-tree mode rapid-pvst
i na portach
SW(config)# interface range f0/1-3
SW(config-if-range)# spanning-tree portfast
```

Polecenie 6 - Zabezpiecz wszystkie urządzenia sieciowe i wprowadź baner MODT : Nieautoryzowany dostęp zabroniony
Przykład:
```
###Przykład:
Urządzenie(config)# enable secret [twoje_hasło]
Urządzenie(config)# line con 0
Urządzenie(config-line)# password [twoje_hasło]
Urządzenie(config-line)# login
Urządzenie(config)# banner motd "Nieautoryzowany dostep zabroniony"
```
