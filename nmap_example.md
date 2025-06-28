
### Comando Base per Ping Sweep

Il comando standard per un ping sweep (host discovery) con Nmap, che disabilita la scansione delle porte, è:

```bash
nmap -sn [target]
```

*   `-sn`: (Scan No port) Disabilita la scansione delle porte. Nmap esegue solo la fase di host discovery per determinare quali host sono attivi.
*   `[target]`: Può essere un singolo IP (`192.168.1.1`), un range (`192.168.1.1-254`) o una notazione CIDR (`192.168.1.0/24`).

---

### Tecniche Avanzate e Scenari Operativi

Un semplice ping (ICMP Echo Request) è spesso bloccato dai firewall. Un penetration tester deve utilizzare tecniche alternative per mappare una rete.

#### Prospettiva Offensiva (Attack)

L'obiettivo è massimizzare il numero di host scoperti, bypassando i filtri di rete.

1.  **ARP Scan (Rete Locale)**
    *   **Comando:** `nmap -sn -PR [target]`
    *   **Tecnica:** Invia richieste ARP a ogni possibile indirizzo nella subnet. È il metodo più veloce e affidabile all'interno di una rete locale (LAN), poiché non è routabile e opera a Livello 2 (Data Link), bypassando firewall e filtri IP di Livello 3.
    *   **Scenario:** Prima fase di un test interno per mappare rapidamente tutti i dispositivi connessi alla stessa subnet.

2.  **TCP SYN/ACK Ping (Reti Esterne/Filtrate)**
    *   **Comando:** `nmap -sn -PS[port(s)] [target]` (es: `-PS80,443,8080`)
    *   **Comando:** `nmap -sn -PA[port(s)] [target]` (es: `-PA80,443`)
    *   **Tecnica:**
        *   `-PS` (TCP SYN Ping): Invia un pacchetto SYN. Un SYN/ACK o un RST di risposta indicano che l'host è online. È molto efficace perché il traffico TCP verso porte comuni (80, 443) è quasi sempre permesso in uscita da una rete e spesso anche in ingresso verso i server.
        *   `-PA` (TCP ACK Ping): Invia un pacchetto ACK. Utile per bypassare firewall *stateless*. Un host online risponderà con un RST.
    *   **Scenario:** Mappare host attraverso un firewall che blocca ICMP. `-PS` è ottimo per trovare server web, `-PA` per identificare host in generale.

3.  **UDP Ping**
    *   **Comando:** `nmap -sn -PU[port(s)] [target]` (es: `-PU53,161`)
    *   **Tecnica:** Invia un pacchetto UDP a porte specifiche. Se la porta è chiusa, l'host risponde con un messaggio ICMP "Port Unreachable", confermando di essere attivo. Se non si riceve risposta, l'host potrebbe essere attivo (e la porta aperta o filtrata) oppure offline. È meno affidabile ma utile come tecnica supplementare.
    *   **Scenario:** Identificare host che eseguono servizi UDP comuni (es. DNS su porta 53, SNMP su porta 161) quando altre tecniche falliscono.

#### Prospettiva Difensiva (Defense)

L'obiettivo è rilevare e bloccare i tentativi di discovery non autorizzati.

1.  **Rilevamento (Detection)**
    *   **Tool:** IDS/IPS (Snort, Suricata), SIEM (Splunk, ELK, Wazuh).
    *   **Tecnica:**
        *   **Signature-based:** Gli IDS possono avere firme per rilevare l'User-Agent di Nmap o pattern di scansione noti (es. regola Snort `ET SCAN Nmap Ping Scan`).
        *   **Anomaly-based:** Un SIEM può correlare log di firewall e di rete. Un singolo IP sorgente che contatta un gran numero di IP destinazione su porte diverse in un breve lasso di tempo è un indicatore di sweep. Un picco di pacchetti RST o ICMP "Port Unreachable" è un altro forte segnale.

2.  **Prevenzione (Prevention)**
    *   **Firewalling:** Configurare regole di *ingress/egress filtering*. Bloccare tutto il traffico ICMP in entrata da fonti non attendibili. Consentire l'accesso a porte TCP/UDP solo da IP specifici e autorizzati.
    *   **Segmentazione della Rete:** Utilizzare VLAN e ACL per limitare la comunicazione tra diverse zone della rete (es. client, server, DMZ). Questo riduce la superficie d'attacco e limita l'efficacia di un ARP scan a una singola subnet.
    *   **Host-based Firewall:** Configurare firewall a livello di sistema operativo (es. `iptables`, Windows Defender Firewall) per applicare policy granulari e negare risposte a probe inaspettati.

---

### Tabella Riassuntiva (Cheat Sheet)

| Comando                                  | Descrizione Tecnica                                | Scenario d'Uso Principale                                |
| ---------------------------------------- | -------------------------------------------------- | -------------------------------------------------------- |
| `nmap -sn <target>`                      | Default (ICMP Echo, TCP SYN/80, TCP ACK/443)       | Discovery rapido e generico (spesso rumoroso).           |
| `nmap -sn -PR <target>`                  | ARP Ping (Broadcast ARP)                           | **Rete Locale (LAN)**. Veloce, furtivo e affidabile.      |
| `nmap -sn -PS80,443 <target>`            | TCP SYN Ping su porte web                          | Bypassare firewall che bloccano ICMP.                    |
| `nmap -sn -PA80 <target>`                | TCP ACK Ping                                       | Mappare host dietro firewall *stateless*.                |
| `nmap -sn -PE -PS443 -PA80 -PU53 <target>` | Combinazione di probe                              | Massimizzare la probabilità di scoperta su reti complesse. |
| `nmap -sn -T2 <target>`                  | Ping Sweep lento (Polite)                          | Evadere IDS/IPS basati su soglie temporali.              |
-------------------------
