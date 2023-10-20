# Demo App Engine

App Engine consente di fare il deploy di un'applicazione su GCP

Consiglio: creare un nuovo project, eliminandolo elimino tutto ciò che c'è connesso ad esso

Mi posiziono nel nuovo progetto, per lavorarci

Ricerco App Engine. Per ogni servizio devo abilitare le API.
Scelgo la Region dove fare il deploy. Se voglio creare diversi App Engine applications in diverse Regions occorre farlo in diversi projects.

Richiede Language ed Environments.
Una volta creato, procedo con il caricamento della mia applicazione. Cloud Shell-> Open Editor -> Open Folder e carico l'applicazione nell'editor.

All'interno di essa (nella demo fornita), vi deve essere un file app.yaml con indicazioni specifiche per App Engine, in questo caso la versione del runtime di Python.

Una volta caricato devo eseguire una build. Ma prima, mi posiziono nella cartella.

```bash
#Mi posiziono nel giusto project, recuperando l'id dal portale
gcloud config set project "project-id"

#Provo a fare il deploy, che fallirà, ma alcune cose vengono caricate per efficienza
gcloud app deploy


#La risposta mi spiega il problema di mancanza di permessi per l'accesso al bucket dello storage su GCP

#Ricerco in GCP, IAM per la gestione dei permessi. E' stato creato un membro in automatico al quale devo concedere il Role: Storage Object Viewer

#Rifacendo il deploy adesso non fallisce
gcloud app deploy

```

### Spiegazione lunga e lista comandi utili
Quando carico un'applicazione tramite App Engine standard, in background viene creato un deployment package. Questo viene archiviato in Object Storage di GCP. Viene utilizzato un tool di CI/CD, che si chiama Cloud Build, ed è necessario che questo tool possa accedere al deployment package archiviato nel Google Cloud Storage. Devo quindi concedere il giusto privilegio. 

Fasi per deploy app:
1. Settare giusto project
2. posizionarsi nella giusta cartella
3. da GCP concedere i giusti privilegi (Role), da IAM (Identity and Access Management)
4. fare il deploy

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

Se carico una versione nuova, la vecchia continua a funzionare fino a quando la nuova non è pronta. 

Successivamente, se non diversamente specificato, tutto il traffico passa sulla nuova versione.

E' possibile visualizzare l'url della versione attiva 
- gcloud app browse                           

e della versione specifica 
- gcloud app browse --version "version_name"  




