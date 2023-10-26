# Demo GKE e comandi utili

*Creazione di un cluster, creazione di un deployment e service* 

**Di base viene creato un cluster con 3 nodi, 6 vCPUs, 12 GB di vRAM**

Dopo aver definito un nuovo progetto e selezionato questo, creo un nuovo cluster, abilitando le API. Seleziono la modalità Standard, per avere piena gestione. Indico come Location type Zonal (possibile anche Regional) e faccio create. 

La stessa operazione chiaramente si può fare anche da cloud shell, alcuni comandi utili.

N.B Per interagire **sul cluster uso** gcloud container clusters per interagire **nel cluster uso** kubectl

Mi connetto al progetto e al cluster a cui sono interessato, se già definito da console

```bash
- gcloud config set project "project_id"  # set progetto

- gcloud container clusters create "name_cluster"  # per creare cluster da shell

- gcloud container clusters get-credentials "nome_cluster" --zone "nome_zona" --project "nome_project"    # per recuperare dati, cluster creato da console ad esempio. NB Stringa recuperabile da console, oggetto cluster, opzione connect

Una volta creato, interagisco con k8s, per farlo uso kubectl

- kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE  # per creare un oggetto deployment da un'immagine precisa

- kubectl get deployments     # per listato deployments

- kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080 # per esporre questo deployment all'esterno, usando un service di tipo LoadBalancer, che verrà generato

- kubectl get services   # per listato servizi, vi sarà un external-ip (ip pubblico) che unito alla porta e al nome mi permette di raggiungere il microservizio creato

Es.35.184.204.214:8080/hello-world

- kubectl get services --watch curl 35.184.204.214:8080/hello-world    # faccio una request e osservo

    # Scaling manuale pods
- kubectl scale deployment hello-world-rest-api --replicas=3  # scalare il numero di istanze del microservizio, avrò 3 pod 

- gcloud container clusters resize my-cluster --node-pool default-pool --num-nodes=2 --zone=us-central1-c 
  # ridimensionare il numero di nodi e portarlo a 2, devo specificare il nome del node pool che fa parte del cluster, ve ne possono essere diversi. Devo trovarlo sulla console

   # Scaling automatico pods
- kubectl autoscale deployment hello-world-rest-api --max=4 --cpu-percent=70     

# autoscale su risorse usate

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