## Verso Hybrid Cloud in GCP, 3 modi per realizzarlo
- Cloud VPN consente di connettere la rete on-premise alla rete GCP
    - utilizza IPSec VPN Tunnel
    - il traffico viaggia attraverso internet (pubblico)
    - tuttavia è cifrato usando il protocollo Internet Key Exchange (IKE)

    Due tipologie di soluzioni Cloud VPN:

    - HA VPN (SLA di 99.99% di disponibilità e con 2 indirizzi IP public)
        - supportato solo routing dinamico (usando BGP)
    - Classic VPN (SLA di 99.99% di disponibilità, 1 indirizzo IP public)
        - supportato a routing dinamico (BGP) e statico (policy-based e route-based)

-   Cloud Interconnect, connessione fisica ad alta velocità tra on-premise e rete VPC 
    - alta disponibilità e alto throughput
    - due tipi di connessioni possibili: Dedicated (10Gbps o 100Gbps), Partner (da 50Mbps a 10Gbps)
    - dati scambiati in una rete privata (a differenza di Cloud VPN)
    - supporto a Google API e servizi, accessibili da on-premise

    N.B consigliata per alte necessità di banda

-   Direct Peering 
    - Path diretto da on-premises network ai servizi Google
    - Non è un GCP service
 
    N.B Direct Peering NON RACCOMANDATA 
