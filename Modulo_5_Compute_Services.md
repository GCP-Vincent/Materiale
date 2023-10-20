# Exploring Google Cloud Platform Compute Services



Tutti i più importanti Google Cloud Services

- [Google App Engine (GAE)](#app-engine-gae)
- [Google Kubernetes Engine (GKE)](#kubernetes-engine-gke) 
- [Google Cloud Functions (GCF)](#cloud-functions-gcf)
- [Google Cloud Run (GCR)](#cloud-run-gcr)

----
 # App Engine (GAE)
 Prima versione rilasciata nel 2008 
 
 Consente di fare il **deploy** e **scalare** le **applicazioni** in GCP

 Supporta una moltitudine di linguaggi: Go, Java, .NET, PHP, Python, Ruby ecc
 Consente di connettersi facilmente con altri servizi di GCP com (Cloud SQL etc)
 
 **Pagamento** per risorse **provisioniate**

 Features:

- **Automatic load balancing**  & **Auto scaling** (delle applicazioni deployate) 
- **Managed Platform update** & **Application health monitoring**, aggiornamento e monitoraggio,
- **Application versioning**, avere diverse versioni, **Traffic splitting**, indicare dove smistare il traffico sulle diverse versioni

**Compute Engine vs App Engine**

Compute Engine, parliamo di un IAAS, offre più flessibilità ma maggiore Responsabilità. Scelta Image, installare software, scelta hw, accessi e permessi più specifici (Certificates/Firewalls),
disponibilità

App Engine, parliamo di PAAS, meno flessibilità, ma minore responsabilità

**Quale usare?** Dipende dalla situazione, ho qualcosa di già pronto e voglio portarlo subito in Cloud, App Engine. Se voglio avere maggiore controllo però allora devo scegliere Compute Engine (Creare una vm)

**App Engine Environments**

**Standard** -> applicazioni run in un **language specific sandboxes**
- **V1** per supporto a Java, Python, PHP, Go (old versioni)
- **V2** per supporto a Java, Python, PHP, Node.js, Ruby, Go (nuove versioni), consigliata
- Completo isolamento con OS/Disk
- Supporto per **scale down to Zero istanze**. Quindi se non ho traffico posso avere zero istanze running, meno costi

**Flexible** -> applicazioni eseguite in **Docker containers**

- Vengono eseguite su VMs, create con Compute Engine
- Supporto a qualsiasi runtime 
- **Non è possibile scale down to Zero**, almeno un'istanza attiva 
----

## Demo App Engine, lista comandi utili
Segue Link ->  [Demo App Engine](Demo/Demo_App_Engine.md)
Altri comandi utili
```bash
- gcloud config set project "project_id"    # set progetto
- gcloud app deploy              # per deploy applicazione 
- gcloud app services list       # listato servizi
- gcloud app versions list       # listato versioni servizio
- gcloud app instances list      # listato istanze

# deploy versione specifica, per efficienza vengono caricate solo le differenze
- gcloud app deploy --version="version_name"  
- gcloud app browse                           # listato url "attivo", che eroga
- gcloud app browse --version "version_name"  # url 

```
----
# Kubernetes Engine (GKE)

Kubernetes rappresenta lo strumento open source più famoso per orchestrare containers, GKE è il servizio gestito offerto da GCP per Kubernetes.

K8s permette di gestire un cluster, un insieme di nodi, inclusi gli aggiornamenti.

Offre le più importanti features per orchestrare containers:
- Auto scaling
- Service 
- Load Balancer 
- Self Healing
- Zero downtime deployments

**GKE** servizio che consente di gestire Kubernetes

- Pod and Cluster Autoscaling (aggiungere e togliere nodi)
- Cloud Logging e Cloud Monitoring 
- Container-Optimized OS, un OS costruito da Google
- Auto-upgrade 


Nella creazione del cluster, abbiamo due modalità
- **Standard** per avere la piena responsabilità sui nodi, **pay-per-node**

- **Autopilot** per delegare a GKE la gestione del cluster  e **pay-per-pod**

----

## Demo Kubernetes Engine, lista comandi utili 

**Creazione di un cluster, creazione di un deployment e service** 

**Di base viene creato un cluster con 3 nodi, 6 vCPUs, 12 GB di vRAM**

Dopo aver definito un nuovo progetto e selezionato questo. Creo un nuovo cluster, abilitando le API. Seleziono la modalità Standard, per avere piena gestione. Indico come Location type Zonal (possibile anche Regional) e faccio create. 

La stessa operazione chiaramente si può fare anche da cloud shell, alcuni comandi utili.

**N.B Per interagire sul cluster uso gcloud container clusters per interagire nel cluster uso kubectl**

Mi connetto al progetto e al cluster a cui sono interessato, se già definito da console

```bash
- gcloud config set project "project_id"  # set progetto

- gcloud container clusters create "name_cluster"  # per creare cluster da shell

- gcloud container clusters get-credentials "nome_cluster" --zone "nome_zona" --project "nome_project"    # per recuperare dati, cluster creato da console ad esempio. NB Stringa recuperabile da console, oggetto cluster, opzione connect

Una volta creato, interagisco con k8s, per farlo uso kubectl

- kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE  # per creare un oggetto deployment da un'immagine precisa

- kubectl get deployments     # per listato deployments

- kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080 # per esporre questo deployment all'esterno, usando un service di tipo LoadBalancer, che verrà generato

- kubectl get services   # per listato servizi, vi sarà un external-ip (ip pubblico) che unito alla porta e al nome  mi permette di raggiungere il microservizio creato

Es.35.184.204.214:8080/hello-world

- kubectl get services --watch curl 35.184.204.214:8080/hello-world    # faccio una request e osservo

    # Scaling manuale pods
- kubectl scale deployment hello-world-rest-api --replicas=3  # scalare il numero di istanze del microservizio, avrò 3 pod 

- gcloud container clusters resize my-cluster --node-pool default-pool --num-nodes=2 --zone=us-central1-c 
  # ridimensionare il numero di nodi e portarlo a 2, devo specificare il nome del node pool che fa parte del cluster, ve ne possono essere diversi. Devo trovarlo sulla console

   # Scaling automatico pods
- kubectl autoscale deployment hello-world-rest-api --max=4 --cpu-percent=70   # autoscale su risorse usate

    # Internamente viene creato un hpa configuration
- kubectl get hpa  # visualizzare horizontal pod autoscaler

  # Eliminazione

- kubectl delete service hello-world-rest-api   # per eliminare il service

- kubectl delete deployment hello-world-rest-api   # per eliminare il deployment

# Per interagire sul cluster, aggiungere nodi ecc, cambia la tipologia di comandi

 # Scaling automatico nodes del cluster
- gcloud container cluster update cluster-name --enable-autoscaling --min-nodes=1 --max-nodes=10  # per definire un autoscaling a livello di nodi del cluster

- gcloud container clusters delete my-cluster --zone us-central1-c  # per eliminare il cluster, nome e dove si trova

```
----
# Cloud Functions (GCF)
Consente di **eseguire codice in risposta ad un evento**

Risponde alla necessità di voler eseguire del codice quando accade un evento particolare, come il caricamento di un file su Cloud Storage, un error log scritto in Cloud Logging ecc

Codice scritto in Node.js, Python, Go, Java, .NET e Ruby
Nessun problema di scalabilità

- **Pay only for what you use**: Numero di invocazioni, tempo e uso di risorse

- **Time Bound**: nella 1st gen max 540 secondi e 8GB di Ram allocabile, nella 2nd gen max 60 minuti e molta più RAM

- **Ogni esecuzione avviene in istanze separate**, non vi è condivisione diretta

## Demo Cloud Functions 
**Creazione di un oggetto per la risposta ad un evento** 

 Abilito sempre le API connesse al servizio.
 Scelgo la tipologia, ricordando le differenze di memoria allocabile e Time Bound. Indico la Region dove allocare l'oggetto.

 Successivamente nella parte Trigger Type, definisco l'evento scatenante (richiesta http, scrittura nel Cloud Storage ecc) e la tipologia di autenticazione necessaria per poter scatenare eventi, quindi invocazioni autenticate o non. Posso definire la memoria allocata ad eseguire il codice e il timeout per l'esecuzione ecc
 Nella pagina successiva inserisco il codice da eseguire e il tipo di runtime collegato al linguaggio utilizzato.

 Posso testare il codice, vedendo anche log e varie metriche connesse: tempi di risposta, memoria usata ecc.

# Cloud Run (GCR)
Idea di fondo : **"Container to Production in Seconds"**
 
Senza dover creare un cluster, gestirlo, ecc.

Esegui i containers direttamente tramite Cloud Run.

## Demo Cloud Run

**Esecuzione velocissima di un microservizio**, senza dover creare un cluster 

Dopo aver abilitato le API, definisco l'url dell'immagine del container.

Indico il nome e la Region dove voglio eseguirlo.

**Quando allocare le risorse?**
- allocare Cpu **solo quando arriva una richiesta** al microservizio 

- allocarla **sempre**

**Definire auto scaling**

Indicare un minimo numero di istanze a 1 riduce i tempi di cold starts. Se infatti eliminassi tutti i containers sarebbe necessario un breve tempo di avvio.

**Definire traffico** ammesso e tipo di autenticazione per le invocazioni del microservizio

Cloud Run è costruito su uno standard open **Knative**
- Pay-per-use (CPU, Memory,Requests and Networking)

Visto che i **containers** contengono tutto il necessario per essere eseguiti, sono **molto portabili** (Cloud Run, GKE, App Engine ecc)

Cloud Run si integra bene con altri servizi come Cloud Code, Cloud Build, Cloud Monitoring & Cloud Logging

Ogni servizio ha una **revisions** (una versione), è possibile editare il servizio. Quindi posso editare e fare il deploy di una nuova revision. 
Per ogni revision posso vedere info su log e altre metriche. E' possibile anche fare tutto tramite **yaml file**.

Avendo diverse revisions, del mio servizio (microservizio), posso decidere come gestire lo split traffic. 

## Anhtos -> per eseguire cluster Kubernetes dove voglio

Note

N.B Per le immagini, il path qui presente utilizza il forwardslash, windows utilizza il backslash. Se non vengono visualizzate il problema potrebbe essere legato a quello