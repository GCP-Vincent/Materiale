# Digital Trasformation

Le aziende devono adattarsi ai cambiamenti(social,big data, cloud) o vengono distrutte

La Digital Trasformation consiste nell'uso di moderne tecnologie per creare o modificare processi di business ed esperienza utente innovando.

Il cloud consente di realizzare questa digital trasformation, riducendo i costi, riducendo le responsabilità (manutenzione dell'infrastruttura), fornendo scalabilità, performance ecc.

Il cambiamento richiede però abilità (skills), **mindset** e cultura. Quando un'azienda vuole spostarsi in Cloud, deve pensare:
 - Modern Architectures (Microservizi, serverless, containers, Kubernetes)
 - Processi Agile (DevOps,SRE, CI/CD)
 - Personale adatto e con le giuste abilità
 - Sperimentare e innovare, usando l'intelligenza intrinseca dei dati (AI)

## Cloud Mindset


Infrastruttura 
-   (Data Center/Cloud)    
        Acquista/Affitta

Pianificazione 
- (Data/Center)   
  avanti nel tempo/allocabile tutto al bisogno  

Deployment
-   (Data Center/Cloud)    
        VMs/PaaS o Containers o Serverless

Team
-   (Data Center/Cloud)    
        Skill specifiche / T-shaped skills (verticali e orizzontali)

Releases
-   (Data Center/Cloud)    
        manuali / CI-CD con varie opzioni (canary,testo su n macchine non su tutte)
Creazione Infrastruttura
-   (Data Center/Cloud)    
        manuale / IaC

Attitudine
-   (Data Center/Cloud)    
        Evitare i fallimenti / Move fast by reducing cost of failure (si ottiene con l'automazione dei test, dei rilasci, della creazione dell'infrastruttura e monitoraggio)

# Modernizzazione Infrastruttura

- Lift and shift: Muoversi sull'infrastruttura Cloud

    es.
    - fare uso di VDI* (virtual desktop infrastructure) in cloud 
    - backup e disaster recovery
    - VMware as a service, usando Google Cloud VMware engine per spostare l'infrastuttura
    - Bare Metal Solution: Spostare workloads specifici (SAP HANA, Oracle db) che necessitano alte performance
    - Migrate for Compute Engine: Migrare VMs e VM storage in GCE


Questo porta a dei benifici: 
- costi, e riduzione del focus sull'infrastruttura. 

Ma non si ottengono tutti i benefici del Cloud (Servizi gestiti, serverless, AI ecc)

# Modernizzazione Applicazione

- Migrare a PaaS o Serverless, anzichè migrarla così com'è:
    - containerizzazione (per utilizzare servizi come Cloud Run)
    - Container Orchestration (GKE, Anthos)
    - Usare cloud dabases e 
    - Usare metodologie DevOps e SRE (automazione e monitoraggio)

Questo porta a dei benifici: 
- servizi gestiti semplificano la manutenzione e il ciclo di vita
- innovazione, usando machine learning e AI 










**Nota**:

Nella VDI*, un hypervisor segmenta i server in macchine virtuali che, a loro volta, ospitano i desktop virtuali a cui gli utenti accedono in remoto dai loro dispositivi. È possibile accedere a questi desktop virtuali da qualsiasi posizione o dispositivo e tutta l'attività di elaborazione viene effettuata sul server host
