# Demo App Engine

**App Engine consente di fare il deploy di un'applicazione su GCP, velocemente**

Consiglio: creare un nuovo project, in questo modo eliminandolo elimino tutto ciò che c'è connesso ad esso. Inoltre bisogna ricordare che posso avere una sola applicazione per progetto, ma posso avere diversi servizi su di essa e diverse versioni e istanze di questi servizi. 

Procediamo
Dopo aver creato dal portale il nuovo progetto (project-> new project) mi posiziono nel nuovo progetto, per lavorarci.
Ricerco, nella barra di ricerca, App Engine. Occorre ricordare che per ogni servizio in GCP devo abilitare le API, quindi dovrò abilitare anche le API per App Engine. Api Admin

Durante la creazione della risorsa App Engine, scegliere la Region dove fare il deploy dell'applicazione, questa è permanente. Posso avere una applicazione per ogni project. Se voglio creare diverse applicazioni tramite App Engine, in diverse Regions, occorre farlo quindi in diversi projects.

Al passo successivo viene richiesto di scegliere Language (dell'applicazione) ed Environments (di App engine).

Una volta creato, procedo con il caricamento della mia applicazione. Per caricarla utilizzo il terminale della console. Apro quindi il terminale (cloud shell) e da qui apro il suo editor. Si apre una versione visual studio code nel browser, sul quale lavorare

Cloud Shell-> Open Editor -> Open Folder e carico l'applicazione nell'editor. (Se ci sono problemi cambiare browser)

All'interno di essa (nella demo fornita), vi è una folder con l'applicazione e due servizi (di prova). Deve esserci un file app.yaml con indicazioni specifiche per App Engine, in questo caso la versione del runtime di Python. Questo file sarà poi quello usato per creare la build

Una volta caricata la cartella nell'editor, posso vederne il contenuto prima di effettuare la build. 

Prima di fare la build tramite cloud shel, mi posiziono nel giusto progetto e nella cartella desiderata da cli. Segue procedura completa

```bash
# Mi posiziono nel giusto project, recuperando l'id del progetto dal portale GCP
gcloud config set project "project-id"

# Provo a fare il deploy, che fallirà, andando a leggere se non diversamente specificato un file che si chiama "app.yaml". Se in questo file non è specificato il nome del service, ad esso verrà assegnato il nome "default". Alcune cose vengono caricate per efficienza, fallirà solo la build
gcloud app deploy

# La risposta mi spiega perchè è fallito il deploy: mancanza di permessi per l'accesso al bucket dello storage su GCP. In pratica mancanza di permessi del service account su Google Cloud Storage

# Ricerco in GCP, IAM, per la gestione dei permessi. E' stato creato un membro in automatico al quale devo concedere anche il Role: Storage Object Viewer. Quindi devo attribuire a questa risorsa, service account, il permesso di lettura. Una volta applicato posso ritornare in cloud shell e riprovare il deploy

# Rifacendo il deploy adesso non fallisce
# Se non diversamente specificato, al servizio verrà assegnato un nome casuale di default
gcloud app deploy

```

### Spiegazione lunga dell'errore e lista comandi utili
Quando carico un'applicazione tramite App Engine standard, in background viene creato un oggetto deployment package che viene archiviato in Object Storage di GCP. Viene utilizzato un tool di CI/CD, che si chiama Cloud Build, ed è necessario che questo tool possa accedere all'oggetto deployment package archiviato nel Google Cloud Storage. Devo quindi concedere il giusto privilegio. 

Fasi per deploy app:
1. Settare giusto project
2. Posizionarsi nella giusta cartella
3. Da GCP concedere i giusti privilegi (Role), da IAM (Identity and Access Management)
4. Fare il deploy

Altri comandi utili
```bash
- gcloud config set project "project_id"    # set progetto, appare sul prompt tra parentesi il nome del progetto se tutto ok
- gcloud app deploy              # per deploy applicazione, il file app.yaml contiene la configurazione, se file diverso va specificato 
- gcloud app services list       # listato servizi
- gcloud app versions list       # listato versioni servizio
- gcloud app instances list      # listato istanze

# deploy versione specifica di un servizio, per efficienza vengono caricate solo le differenze
- gcloud app deploy --version="version_name"  
- gcloud app browse                           # url della versione "attiva", che eroga
- gcloud app browse --version "version_name"  # url della versione specifica 

```

Se carico una versione nuova, la vecchia continua a funzionare fino a quando la nuova non è pronta (diverse versioni possono coesistere) 

Successivamente, se non diversamente specificato, tutto il traffico passa sulla nuova versione. 

E' possibile visualizzare l'url della versione attiva, per aprirla nel browser
- gcloud app browse                           

e della versione specifica 
- gcloud app browse --version "version_name"  
