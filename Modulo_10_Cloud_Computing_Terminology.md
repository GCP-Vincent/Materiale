# Terminologia ricorrente
- Public
- Private 
- Hybrid

## Public Cloud

Quando "hosti" tutto nel cloud.
- Quindi non hai necessità di un datacenter
- Nessun capitale iniziale necessario, (diciamo)
- Possibilità di scalare molto e velocemente 
- Le risorse hardware sono gestite dal Cloud Provider, quindi rotture, rete e sicurezza del data center
- Queste risorse sono condivise tra molteplici clienti finali

## Private Cloud

Quando "hosti" tutto nel tuo datacenter.
- Hai necessità di un datacenter
- Capitale iniziale necessario, per acquisto e manutenzione
- Pianificazione per scalare la propria infrastrutura (tempo e risorse). Quindi ad esempio i picchi di carico vanno pianificati



## Hybrid Cloud

Combinazione di entrambi
- Utilizzo di Public Cloud per alcuni carichi di lavoro e Private per altri
- Ad esempio utilizzi Google Cloud Dataflow per processare un data stream (come i logs) generati dalle applicazioni on-premise. O connettere le applicazioni on-premise al Google Cloud SQL database
- Sicuramente vi è il vantaggio di avere flessibilità, scegliento cosa usare e dove
- Svantaggio principale, l'incremento della complessità utilizzando due modalità diverse


# Multi Cloud
Utilizzo di piattaforme Cloud diverse, con o senza un'infrastruttura on-premise.
- Sicuramente ancora maggiore flessibilità ma anche 
- Maggiore complessità 

## Verso Hybrid Cloud in GCP, 3 modi
- Cloud VPN consente di connettere la rete on-premise alla rete GCP
    - utilizza IPSec VPN Tunnel
    - il traffico viaggi attraverso internet (pubblico)
    - tuttavia è cifrato usando il protocollo Internet Key Exchange (IKE)

    Due tipologie di soluzioni Cloud VPN:

    - HA VPN (SLA di 99.99% di disponibilità e con 2 indirizzi IP public)
        - supportato solo routing dinamico (usando BGP)
    - Classic VPN (SLA di 99.99% di disponibilità, 1 indirizzo IP public)
        - supportato a routing dinamico (BGP) e statico (policy-based e route-based)

-   Cloud Interconnect, connessione fisica ad alta velocità tra on-premise e VPC rete 
    - alta disponibilità e alto throughput
    - due tipi di connessioni possibili: Dedicated (10Gbps o 100Gbps), Partner (da 50Mbps a 10Gbps)
    - dati scambiati in una rete privata (a differenza di Cloud VPN)
    - supporto a Google API e servizi, accessibili da on-premise

    N.B consigliata per alte necessità di banda

-   Direct Peering 
    - Path diretto da on-premises network ai servizi Google
    - Non è un GCP service

    N.B NON RACCOMANDATA 

    Note
N.B Per le immagini, il path qui presente utilizza il forwardslash, windows utilizza il backslash. Se non vengono visualizzate il problema potrebbe essere legato a quello