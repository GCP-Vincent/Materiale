# Cloud computing
Partiamo dalla definizione del NIST, National Institute of Standards and Technology.

**Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared 
pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that 
can be rapidly provisioned and released with minimal management effort or service provider interaction.** 

**This cloud model is composed of five essential characteristics , three service models, and four deployment models**.

https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-145.pdf


Caratteristiche essenziali: On-demand self-service, Broad network access, Resource pooling, Rapid elasticity, Measured service


I tre principali di Service Models, ognuna con un diverso grado di gestione lasciata all'utente: 

**Infrastructure-as-a-Service (IaaS)**

**Platform-as-a-Service (PaaS)** 

 **Software-as-a-Service (SaaS)** 
 
Con as-a-Service si indica in genere un servizio di cloud computing gestito da un provider esterno per conto dell'utente



# Terminologia ricorrente
- [IaaS](#iaas)
- [PaaS](#paas) 
- [SaaS](#saas)
- [Public Cloud](#public-cloud)
- [Private Cloud](#private-cloud) 
- [Hybrid Cloud](#hybrid-cloud)
- [Multi Cloud](#multi-cloud)
- [Microservices](#microservices)
- [Orchestrator](#orchestrator)


# Service Models
![Alt text](/Images/as-a-Service.png)

## IaaS

Infrastructure-as-a-Service, o IaaS, offre un primo livello di delega della gestione dell'infrastruttura on-premise. Si tratta di un servizio con modello di consumo pay-as-you go, in cui una terza parte fornisce i servizi di infrastruttura, come lo storage e la virtualizzazione, quando sono necessari, tramite cloud e Internet. 

**L'utente è responsabile del sistema operativo e dei dati, delle applicazioni, del middleware e dei runtime (Java, Python ecc), mentre il provider offre l'accesso e la gestione di rete, server, virtualizzazione e storage.**

«Per middleware si intende il software che rende accessibile sul Web risorse hardware o software che prima erano disponibili solo localmente o su reti non Internet.» (https://it.wikipedia.org/wiki/Middleware)


Il middleware è un software che risiede tra un sistema operativo e le applicazioni eseguite in esso. Il middleware, che essenzialmente funziona come un livello di traduzione nascosto, consente la comunicazione e la gestione dei dati per le applicazioni distribuite(https://azure.microsoft.com/it-it/resources/cloud-computing-dictionary/what-is-middleware)

Non occorre gestire o aggiornare il datacenter in sede, attività di cui si occupa il provider. L'utente ha il controllo completo dell'infrastruttura grazie a un'interfaccia di programmazione delle applicazioni (API) o a un dashboard. 

IaaS garantisce notevole flessibilità, consentendo di acquistare solo i componenti che servono, aggiungendoli o eliminandoli quando e come necessario. Con spese fisse ridotte e senza costi di manutenzione, il servizio IaaS risulta molto conveniente. 

Costituisce un metodo rapido e flessibile per creare e poi dismettere ambienti di test e sviluppo. È possibile utilizzare solo l'infrastruttura necessaria per creare l'ambiente di sviluppo, ingrandirla o ridurla per il tempo necessario, fermandosi una volta ottenuto quanto desiderato e pagando solo per i servizi utilizzati. 

IaaS presenta anche alcuni inconvenienti, ad esempio i potenziali problemi legati all'affidabilità dei servizi, alla sicurezza del provider e alla presenza di sistemi multitenant in cui il provider deve condividere le risorse dell'infrastruttura con più clienti. Sono tuttavia problematiche che possono essere evitate scegliendo un provider affidabile e qualificato, con un'esperienza e una reputazione consolidate. 

Sono validi esempi di IaaS provider di cloud pubblico quali AWS, Microsoft Azure e Google Cloud.

**Quindi dal OS, incluso, in su è gestione dell'utente**, aggiornamenti a carico dell'utente

## PaaS

Platform-as-a-Service, o PaaS offre un ulteriore livello di astrazione rispetto alla gestione completa e on premise dell'infrastruttura. Prevede che hardware e software siano ospitati nell'infrastruttura del provider, che distribuisce la piattaforma all'utente come soluzione integrata, stack di soluzioni o servizio erogato tramite una connessione internet.

Pensato principalmente per sviluppatori e programmatori, il servizio PaaS offre una piattaforma su cui l'utente può sviluppare, eseguire e gestire applicazioni senza dover creare e gestire l'infrastruttura o la piattaforma normalmente associate a tali processi. 

L'utente si dedica quindi alla scrittura di codice, crea e gestisce le app, ma senza doversi poi occupare degli aggiornamenti software o della manutenzione dell'hardware. Il provider offre l'ambiente in cui creare e distribuire le app, autoscaling, availability & load balancing ecc. 

Il servizio PaaS consente agli sviluppatori di creare un framework in cui realizzare e personalizzare le applicazioni web, a partire da componenti software integrati, riducendo così la quantità di codice che devono scrivere.


**Quindi dall'applicazione, esclusa, in su è gestione dell'utente**, no aggiornamenti 

## SaaS
Software-as-a-Service, o SaaS, anche noto come servizi applicativi cloud, è la forma più completa di servizi di cloud computing, e consiste nella fornitura di un'intera applicazione gestita da un provider tramite un browser web. 

Il provider si occupa degli aggiornamenti software, della correzione dei bug e di altre attività generiche di manutenzione del software, mentre l'utente si connette all'app tramite un'API o un dashboard. Non è prevista l'installazione di software sulle singole macchine e l'accesso dei gruppi al programma è più lineare e affidabile. 

Se, ad esempio, disponi di un account email di un servizio web come Outlook o Gmail, avrai già una certa dimestichezza nell'utilizzo di SaaS poiché è come accedere al tuo account e utilizzare la tua posta da qualsiasi dispositivo. 

SaaS è un'opzione ottimale per le piccole aziende che non hanno il personale o la larghezza di banda sufficiente per gestire installazioni e aggiornamenti software, o per le applicazioni che richiedono un livello minimo di personalizzazione, o che vengono utilizzate solo sporadicamente. 

I vantaggi offerti da SaaS in termini di tempo e manutenzione possono essere tuttavia controbilanciati da problemi legati a controllo, sicurezza e prestazioni. Per questo è importante scegliere un provider altamente affidabile.

**Quindi solo inserimento dati è gestione dell'utente**

Altre varietà che stanno nel mezzo

**Containers as a Service (Caas) e Function as a Service (FaaS)**

# Deployment Models


## Public Cloud

Quando "hosti" tutto nel cloud, nel datacenter di un altro.
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

Combinazione di entrambi private-public
- Utilizzo di Public Cloud per alcuni carichi di lavoro e Private per altri
- Ad esempio utilizzi Google Cloud Dataflow per processare un data stream (come i logs) generati dalle applicazioni on-premise. O ancora connettere le applicazioni on-premise con Cloud SQL database
- Sicuramente vi è il vantaggio di avere flessibilità, scegliendo cosa usare e dove
- Svantaggio principale, l'incremento della complessità utilizzando due modalità diverse


## Multi Cloud
Utilizzo di piattaforme Cloud diverse (AWS,AZURE,GCP), con o senza un'infrastruttura on-premise.
- Sicuramente ancora maggiore flessibilità ma anche 
- Maggiore complessità 

## Community Cloud (Poco usato)
 Si tratta di un modello di servizio multi-tenant e federato tra diverse organizzazioni che hanno requisiti simili e simili obiettivi business.

Questo tipo di cloud è gestito da tutti i partecipanti o da un provider esterno supra partes.


# Microservices

Le enterprises si stanno muovendo verso le architetture a microservizi.
Anzichè avere un'applicazione monolite, avere piccoli microservizi

Il grande vantaggio con essi è infatti la flessibilità di innovazione, è infatti possibile sviluppare applicazioni in diversi linguaggi di programmazione (Go, Java, Python, Javascript ecc)

Chiaramente questa flessibilità porta complessità nel deployment. Sarebbe comodo avere un unico modo per realizzare il deployment di questi microservizi (potenzialmente scritti in linguaggi diversi). 

Ecco che ci vengono in soccorso i containers Docker,  tecnologia dei containers appartenente al mondo Linux. E' possibile creare delle Docker images per ogni microservizio. 
Questa image contiene tutto il necessario per eseguire un microservizio:
- Application Runtime (JDK o Python o NodeJS ecc)
- Application code e dipendenze

Questa image posso eseguirla in qualsiasi infrastruttura:
- Local machine
- Datacenter
- Cloud, di qualsiasi cloud providers

Un altro grande vantaggio, oltre alla portabilità, è dato dalla leggerezza, se paragonato alle Virtual Machines. Nelle VMs in aggiunta all' host OS, ho anche un Guest OS per ogni VM. Con i containers quest'ultimo non è necessario.

I containers sono inoltre isolati, gli uni dagli altri. 

![Alt text](/Images/VMs vs containers.png)

# Orchestrator

Chiaramente al crescere del numero dei containers, diventa irrealistico gestirli manualmente. Ecco che diventa necessario utilizzare uno strumento che possa gestirli. L'orchestatore (es. Kubernetes)

L'orchestratore tipicamente offre:
- Auto scaling: aumenta e decrementa il numero di containers on demand
- Service discovery: aiuta i microservizi a trovarsi tra di loro, devono comunicare
- Load balancer: per distribuire il carico tra di essi
- Self healing: per osservarne lo stato e rimpiazzare quelli falliti
- Zero downtime deployments: rilasciare nuove versioni senza downtime


Tutti i principali cloud provider forniscono servizi gestiti di Kubernetes (EKS di AWS, GKE per Google, AKS per Azure)


![Alt text](/Images/orchestrator.png)
