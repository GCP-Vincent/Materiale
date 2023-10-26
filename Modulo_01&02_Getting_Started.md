# Google Cloud Platform (GCP)

Piattaforma Cloud gestita da Google che mette a disposizione oltre 200 services

# Cos'è il Cloud e perché ne abbiamo bisogno

Prima del cloud, i picchi di richieste imponevano acquisti e predisposizioni preventive. Di conseguenza

- Costi, non sempre sostenibili (es. startup)
- Sovradimensionamento nei periodi "morti"

Il cloud permette di ottenere risorse on-demand (su richiesta)
- Quando servono
- Pagando per quello che uso
- Senza costi per la manutenzione dell'infrastruttura
- Diventando globale in pochi minuti

I principali attori in questo mondo, quindi i maggiori cloud providers, sono: Amazon, Microsoft, Google (in ordine di porzione di mercato)

E' possibile fare una account di prova su tutte le piattaforme, in particolare per Google Cloud Platform, la prova concede 300$ di crediti e l'uso di oltre 20 servizi.

# Zones & Regions
Alcuni termini che ritroviamo spesso, che cambiano di poco, in termini numerici, in base al cloud provider, sono quelli di Region e Zone.

Questi concetti sono necessari per avere

- Low latency: vogliamo fare in modo che utenti dislocati in parti del mondo diverse, accedano ai servizi in tempi rapidi. 

Come? Erogando il servizio in Regions diverse

    - In questo modo, gli utenti vicini ad una Region accedono a quella
    - Se un datacenter va giù ne ho un altro nella stessa Region
    - Se l'intera Region non è disponibile, continuo ad erogare da altre

- High availability (HA): vogliamo rendere molto disponibile il nostro servizio.

Come? Erogandolo in Zones diverse

## Region
Ad oggi ci sono 38 Regions in GCP. Ogni Region dispone di 3 Zones, almeno.

Rappresenta quindi un'area che ospita le tue applicazioni.

Le Zones nella stessa Region sono connesse a bassissima latenza. 

## Zone
Ad oggi 115 Zones. Una Zone è un datacenter. Ogni Zone dispone di almeno 1 cluster, ovvero un insieme di risorse hosted in un datacenter. 

![Alt text](Images/Regions_zones.png)




Note

N.B Per le immagini, il path qui presente utilizza il forwardslash, windows utilizza il backslash. Se non vengono visualizzate il problema potrebbe essere legato a quello