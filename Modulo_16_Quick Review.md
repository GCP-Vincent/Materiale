# Breve riassunto dei principali servizi visti in GCP

## Basic Compute Services in GCP

- Google Compute Engine 
    -       Windows o Linux VMs (IaaS)
- Preemptible VMs 
    -       Short-lived VMs per non time-critical workloads
- Sole-tenant Nodes   
    -       Hardware dedicato
- VMWare Engine      
    -        Per eseguire VMWare workloads in Google Cloud
- MIG             
    -       Per creare molteplici VMs speculari
- Cloud Load Balancing 
    -       Per bilanciare il carico su molteplici istanze di un applicazione o servizio. Tipicamente è considerato come una soluzione di rete   

## Managed Compute Services in GCP
- App Engine 
    -       Per il deployment di web apps veloce e scalabile (PaaS, Serverless)
- Cloud Run  
    -       Per eseguire containers in produzione in secondi. (CaaS, Serverless)
- GKE   
    -       Managed Kubernetes Service. Fornisce orchestrazione dei containers (CaaS) 

- Cloud Functions
    -       Compute per rispondere ad eventi. (Serverless)

- Anthos
    -      Per gestire cluster Kubernetes in multi-cloud e on-premises

- Firebase
    -      Per creare App per IoS, Android, Web, C++ e Unity


## Storage - Managed Services in GCP
- Persistent Disk, diverse tipologie
    -       Block storage per le tue VMs
- Local SSD  
    -        Disco effimero block storage per le tue VMs
- Cloud Filestore   
    -       File share nel Cloud
- Cloud Storage
    -       Object storage nel Cloud 


## Database - Managed Services in GCP
- Cloud SQL  
    -       Database Regional Relazionale OLTP (MySQL, PostgreSQL, SQL server)
- Cloud Spanner 
    -       Database Global Relazionale OLTP. Scalabile 99.999% di disponibilità 
- Cloud Firestore (ex Datastore)   
    -       Per applicazioni che hanno una struttura mutevole velocemente (schema-less). Serverless transactional document DB, supporta app web e mobile. Capacità (0-pochi TBs)
- Cloud BigTable
    -       Large databases (10 TB- PBs). Streaming, analytical & operational workloads. Non è serverless, occorre definire il cluster
- Cloud Memorystore
    -       In memory databases/cache. Per applicazioni che necessitano di risposte in microsecondi
## Streams, Analytics, Big Data & .. - Managed Services in GCP
- Cloud Pub/Sub
    -       Per avere una gestione asincrona dei messaggi
- BigQuery
    -       Relational OLAP databases. Per Datawarehousing e BigData workloadsDatabase  
- BigQuery ML    
    -       Per usare Machine Learning usando BigQuery 
- Cloud Dataflow
    -       Elaborazione unificata dei dati in modalità flusso e batch serverless, veloce e conveniente
- Cloud Dataproc
    -      Utilizza Dataproc per la modernizzazione dei data lake, l'ETL e attività di data science sicure su scala mondiale, completamente integrati con Google Cloud a un costo molto inferiore. Non è serverless
- Cloud Data Fusion 
    -       Un servizio completamente gestito per l'integrazione dei dati cloud-native su qualsiasi scala.
- Data Studio
    -       Visualizzare dati
- Looker 
    -       Piattaforma di business intelligence unificata. Self-service. Regolata. Incorporata.  


## Migration - Managed Services in GCP
- Database Migration Service
    -       Per migrare dati da on-premise o da un cloud provider verso CloudSQL 
- Storage Transfer Service   
    -       Online Transfer verso Cloud Storage (quindi buckets)     
- Transfer Appliance    
    -       Trasferimento fisico usando un dispositivo 
- Migrate for Compute Engine 
    -       Per migrare VMs e VM storage in GCE da VMware on premise o altri cloud provider 
- Migrate for Anthos  
    -       Per migrare VMs verso GKE 
- BigQuery Data Transfer Service
    -       Per migrare verso BigQuery  