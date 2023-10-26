# Total Cost of Ownership (TCO)

Come stimare i costi che si risparmiano passando al Cloud?
- Ricavando i TCO:
    - Costi infrastruttura (acquisto server,db,storage,rete)
    - Costi manutenzione della stessa 
    - Costo personale
    - Costo licenze
    - Costo elettricità ecc

Successivamente confrontare il tutto con il costo in Cloud 


## Consumption-based vs Fixed-price Pricing Models
Vi sono due modelli di pricing usati nel Cloud

- Consumption-based: pago quello che uso

   -  es. Cloud functions: paghi per numero di invocazioni

- Fixed-price: pago per istanze, che vengano usate o meno 

   - es. Compute Engine: predispongo un VM, pago per istanza
    
## CapEx vs OpEx
Separazione in categorie di costi
- Capital Expenditure (CapEx): soldi spesi per comprare infrastruttura (crescita azienda) 

    - costi addizionali di manutenzione
    - costi personale che la gestisce

         - es. leasing software, acquisto servers
    
- Operational Expenditure (OpEx): soldi per usare un servizio o prodotto (gestione)
    - zero costi iniziali
    - paghi in base all'uso (pay-as-you-go model)
        - es. Cloud Functions: pago per numero di invocazioni del codice


## Come incide il costo

- Tipo di risorse e configurazione : memoria, cpu, access tier  (storage) ecc
- Utilizzo: Quanto la VM è running, quanto traffico ingress ed egress, numero invocazioni di Cloud Function ecc
- Quale Region: il prezzo varia per Region
- Trasferimento dati: Ingress ed Egress, dati da on-premise a GCP sono free. Il viceversa no.

**Google Cloud Calculator** è un ottimo strumento per stimare i costi in base alle specifiche

*N.B Traffico nella stessa Zone non si paga, ma se due applicazioni comunicano e si trovano in Regions diverse c'è un costo sul traffico. Quindi non tutto il traffico è free*

## GCP Cost Management

La sezione Billing contiene un sacco di strumenti per gestire il costo dei servizi in GCP. 
- **Cost Billing Reports**: fornisce una panoramica generale sui costi, trend sul project ecc
- **Cost Table report**: permette di andare più in dettaglio
- **Cost breakdown**: per visionare i dettagli su costi e promozioni 
- **Budgets and alerts**: per settare un budget e definire alerts in base a soglie indicate
- **Commitments**: consente di visionare le risorse committate (1-3 anni)
- **BigQuery Export**: per inviare i dati verso BigQuery e analizzarli 
- **Account management**: per gestire i progetti connessi al billing account. E' possibile definire molteplici billing accounts da associare ai projects, cliccando su di esso

## Best Practices

- **Raggruppa le risorse** in folders e projects, utilizza labels. Per avere una visione ad alto livello
- Almeno settimanalmente **analizza l'andamento dei costi**
- **Stima i costi** prima del deployment (Google Cloud Calculator)
- Usa le funzionalità di **Cost Management**
    - cost table reports, budgets e cost alerts ecc
- **Stoppa le risorse** che non sono necessarie 
- Utilizza **VMs preemptible** se i workloads sono non critici
- Utilizza VMs per 1-3 anni (**Committed use discounts**)
- PaaS , **utilizzare servizi gestiti**, esclude i costi di gestione di IaaS
- **Includi tutti i teams** nella gestione dei costi, per tenerli bassi