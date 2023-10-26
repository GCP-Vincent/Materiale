# What is Cloud Native?

La tecnologia cambia, con essa anche l'architettura evolve. Uno dei più importanti cambiamenti negli ultimi anni è stato l'arrivo del Cloud. 

Occorre quindi adottore una nuova architettura se si vuole sfruttare il meglio dal cloud e utilizzare una architettura Cloud Native.


Questo tipo di architettura ci permette di cogliere il meglio dal Cloud, per via della sua natura di essere elastico (scaling) e distribuito. 

L'obbiettivo è quello di aumentare la velocità di delivery del software (da dev a production), e aumentare l'affidabilità del servizio riducendo i problemi in produzione (move fast by reducing cost of failure) attraverso la collaborazione dei vari teams.

## Pilastri

- Microservices: piccoli microservizi che parlano tra loro, gli aggiornamenti impattano in maniera limitata e sono più veloci da implementare

- Containers: contengono codice e tutto il necessario per essere eseguiti ovunque. Sono quindi portabili, build-once run anywhere. Inoltre sono molto veloci da eseguire

- Container Orchestration: Kubernetes, un orchestator consente di gestire al meglio i containers.

- DevOps: è molto importante avere collaborazione ed utilizzare processi di CI/CD e IaC per automatizzare molti dei processi.

Cosa non è Cloud Native? 

Usare VMs, fare deployments manuali, creare infrastruttura manualmente sul Cloud. 

### Servizi in GCP che usano Containers

- Cloud Run: per fare il deploy di applicazioni containerizzate, senza necessità di un cluster. (CaaS)(Serverless)

- Google Kubernetes Engine: per orchestrare containers con Kubernetes, necessità di un cluster. (CaaS)

- Anthos: Gestisci Kubernetes cluster in multi-cloud e on-premises.    (Hybrid Cloud)


### Servizi in GCP che Serverless

Serverless: Il serverless computing è un modello di sviluppo cloud native che consente agli sviluppatori di creare ed eseguire applicazioni senza gestire i server.
Quindi non occorre preoccuparsi dei server, della allocazione dei servers.  Si paga solo il consumo. 

- Cloud Functions: Serverless compute per rispondere a particolari eventi. Esecuzione di funzioni (o codice) in risposta ad eventi (dato archiviato, messaggio in Pub/Sub ecc). In base al carico Google Cloud Functions scala

- Cloud Run: Per eseguire containers in produzione velocemente, senza un orchestator. 
- Cloud Firestore (ex Datastore): Utile per le applicazioni la cui struttura evolve velocemente (schema-less). Serveless transactional document DB, supporta mobile e web apps. Da 0-few TBs di dati. Non occorre fare il provisioning dei servers, creo documenti e collection e inizio ad archiviare i dati.
- Cloud Dataflow: Elaborazione unificata dei dati in modalità flusso e batch serverless, veloce e conveniente.
- Cloud Pub/Sub: Per avere una gestione dei messaggi in maniera asincrona non bloccante. Paghi per numero di messaggi
- BigQuery: Relational OLAP, Data warehousing e BigData workloads. Paghi per dati archiviati e queries eseguite. 



## Data Formats

- Structured: Tabelle, Righe, Colonne e Relazioni (dati che hanno uno schema fisso)
    - Esempi: Informazioni su ordini, inventario ecc
        - Google Cloud Services: CloudSQL (Regional Transactional), Cloud Spanner (Global), BigQuery 

- Semi Structured: Schema flessibile
    - Key-Value, Document(JSON) - informazioni profili social media ad esempio
        - Google Cloud Services: Cloud Firestore/Datastore   

- Unstructured: Video, Audio,Image, Text, Binary files
        
    - Google Cloud Services: Cloud Storage (dati nei buckets)

N.B 
    
    BigQuery può essere usato anche per archiviare dati Semi strutturati o tramite BigQuery ML essere usato su dei dati senza struttura (come immagine, video) per fare machine learning 

## Scelta Regions e Zones

Vi sono diverse motivazioni nella scelta delle Regions e Zones:
1. Compliance: Per motivi di regolamentazioni e standards
    
    Es. Alcuni Paesi non consentono che i dati dei loro cittadini vengano archiviati in altri Paesi
2. Latenza e Performance: Essere vicini agli utenti o alle applicazioni (se un'applicazione usa un db, è importante che i due siano vicini)
    - Premium Tier, piano per avere ottime performance di rete ma costoso (private Google Cloud network)
    - Standard Tier, traffico su internet
3. Fault Tolerance: Distribuire su diverse Regions per avere HA
4. Prezzo: Il prezzo cambia da Region a Region

.... ecc