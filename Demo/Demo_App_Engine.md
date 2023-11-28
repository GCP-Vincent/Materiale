# Demo App Engine

**App Engine consente di fare il deploy di un'applicazione su GCP, velocemente**

Consiglio: creare un nuovo project, in questo modo eliminandolo elimino tutto ciò che c'è connesso ad esso. Inoltre bisogna ricordare che posso avere una sola applicazione per progetto, ma posso avere diversi servizi su di essa e diverse versioni e istanze di questi servizi-

Dopo aver creato dal portale il nuovo progetto mi posiziono nel nuovo progetto, per lavorarci.

Ricerco App Engine. Per ogni servizio in GCP devo abilitare le API, quindi dovrò abilitare anche le API per App Engine. Api Admin

Durante la creazione della risorsa App Engin, scegliere la Region dove fare il deploy dell'applicazione, questa è permanente. Posso avere una applicazione per ogni project. Se voglio creare diverse App Engine applications in diverse Regions occorre farlo quindi in diversi projects.

Al passo successivo viene richiesto di scegliere Language (dell'applicazione) ed Environments (di App engine).

Una volta creato, procedo con il caricamento della mia applicazione. Per caricarla utilizzo il terminale della console. Aprendo l'editor si apre visual studio code, sul quale lavorare

Cloud Shell-> Open Editor -> Open Folder e carico l'applicazione nell'editor. (Se ci sono problemi cambiare browser)

All'interno di essa (nella demo fornita), vi è una folder con l'applicazione e due servizi. Deve essere un file app.yaml con indicazioni specifiche per App Engine, in questo caso la versione del runtime di Python.
Verrà fatto il deploy di questo.

Una volta caricata la cartella nell'editor. posso vederne il contenuto prima di effettuare la build. 

Una volta caricato devo eseguire una build. Ma prima, mi posiziono nel giusto progetto e nella cartella desiderata da cli.

```bash
# Mi posiziono nel giusto project, recuperando l'id del progetto dal portale
gcloud config set project "project-id"

# Provo a fare il deploy, che fallirà. Alcune cose vengono caricate per efficienza, fallirà solo la build
gcloud app deploy

# La risposta mi spiega perchè è fallito, problema di mancanza di permessi per l'accesso al bucket dello storage su GCP. In pratica mancanza di permessi del service account su GCS

# Ricerco in GCP, IAM per la gestione dei permessi. E' stato creato un membro in automatico al quale devo concedere anche il Role: Storage Object Viewer

# Rifacendo il deploy adesso non fallisce
gcloud app deploy

```

### Spiegazione lunga e lista comandi utili
Quando carico un'applicazione tramite App Engine standard, in background viene creato un oggetto deployment package che viene archiviato in Object Storage di GCP. Viene utilizzato un tool di CI/CD, che si chiama Cloud Build, ed è necessario che questo tool possa accedere all'oggetto deployment package archiviato nel Google Cloud Storage. Devo quindi concedere il giusto privilegio. 

Fasi per deploy app:
1. Settare giusto project
2. Posizionarsi nella giusta cartella
3. Da GCP concedere i giusti privilegi (Role), da IAM (Identity and Access Management)
4. Fare il deploy

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

Se carico una versione nuova, la vecchia continua a funzionare fino a quando la nuova non è pronta (diverse versioni possono coesistere) 

Successivamente, se non diversamente specificato, tutto il traffico passa sulla nuova versione.

E' possibile visualizzare l'url della versione attiva 
- gcloud app browse                           

e della versione specifica 
- gcloud app browse --version "version_name"  




