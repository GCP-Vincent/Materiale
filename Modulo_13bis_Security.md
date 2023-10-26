# Security in GCP

# Modello Zero Trust Security

- Nel modello tradizionale di security: La sicurezza è implementata a livello di perimetro di rete. Ogni cosa dentro è fidata (guscio d'uovo)
- Nel modello Zero Trust invece: "No person or device should be trusted by default, even if they are already inside an organization's network"
    - Tutto il traffico è una minaccia
    - Principio del minimo privilegio
    - Monitoraggio continuo
 
**Vediamo adesso alcuni strumenti che GCP mette a disposizione per la sicurezza**
## Key Management Service

KMS consente di creare, usare, distribuire e gestire chiavi di cifratura (simmetriche e asimmetriche). E' possibile utilizzarle nelle applicazioni e nei servizi GCP

Nella sezione Security, alla voce del Key Management della Blade . Occorre creare un **key ring** (portachiavi), all'interno del quale mettere le chiavi, da utilizzare poi in altri servizi

## Secret Manager

Lo trovo sempre nella sezione Security. 
Permette di gestire e archiviare in modo sicuro API key, passwords, certificati ed altri dati sensibili. Ad esempio la password per connettersi al database, o API keys per parlare con differenti API. 


## Cloud Data Loss Prevention (DLP)

Strumento che consente di cercare, classificare e **mascherare dati sensibili** (numeri di Credit Card, SSNs, passwords in chiaro, credenziali Google Cloud)
Si integra bene con Cloud Storage, BigQuery e DataStore. Fornisce inoltre delle API che possono essere utilizzate dalle applicazioni per ricercare e mascherare dati sensibili

## Cloud Armor

Consente di **proteggere** le applicazioni in produzione **da DOS e attacchi web comuni** (OWASP Top 10, Open Web Application Security Project) come XSS (cross-site scripting, iniettare script) e SQL injection

## Web Security Scanner

Servizio che consente di **identificare** vulnerabilità, come XSS e SQL injection, eseguendo test di sicurezza

## Binary Authorization

Assicura che solo immagini di **containers trust** possano essere deployate in Google Cloud 

## Container Threat Detection

Consente di monitorare attacchi che possono essere portati avanti da containers in runtime (Es. scaricamento di binari spospetti o altro)

## Security Command Center (quadro generale)

Fornisce una **fotografia generale** della sicurezza in Google Cloud. Consente di scoprire **misconfigurazioni e vulnerabilità** (built-in threat detection). Fornisce inoltre un monitoraggio sulla conformità (compliance), fornendo reports.


