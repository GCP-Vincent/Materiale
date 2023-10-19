# Bare Metal in the Cloud

Le VMs create su GCP non hanno un hardware dedicato. In generale una mia VM può trovarsi quindi su di un host nel quale vi sono altre VMs di altre persone. Si sfrutta quindi la virtualizzazione, ovvero la capacità di astrarre dall'hardware sottostante.

 Il software che consente di fare questo è l'hypervisor. Tuttavia questo implica overhead, quindi un consumo di risorse necessario a fare eseguire l'hypervisor stesso. 

Se si vuole evitare di utilizzare un hypervisor, avendo quindi dell'hw dedicato in GCP, e maggiori performance (anche se su questo avrei da ridire), esiste:
- **Bare Metal Solution**: Hardware e nessun software pre-installato
    - Hw dedicato e custom
    - No Hypervisor (migliori performance rispetto alle VMs)
    - Scelta del OS
    - Il cliente è responsabile per licenze, installazione e mantenimento del software 
    - Si utilizza questa modalità se si vogliono usare ad esempio hypervisor di terze parti, applicazioni che necessitano di un accesso a basso livello ecc

# Google Cloud VMware Engine

VMware fornisce soluzioni di virtualizzazione. Molto popolare nelle enterprises. 

Come sposare i workloads sul cloud senza troppo sforzo?

    Google Cloud VMware Engine: 
    - Per espandere e migrare (Lift and shift) l'infrastruttura VMWare su Google Cloud. Quindi migrare VMWare workloads in cloud
    - Non occorre apportare nessun cambiamento ad applicazioni, tools o processi
    - Anche dopo la migrazione è possibile usare i tools VMware esistenti
    - Nessun problema di hw o licenze
    - Utilizzo delle alte performance di rete Google
    - Semplice connessione con altri Google Cloud services (come Cloud SQL, BigQuery ecc)
    - Al termine i workloads vengono eseguiti in un'infrastruttura dedicata

# Migrate for Compute Engine

Per migrare in generale, VMs e VM storage verso GCE, da VMWare o anche da altri Cloud Provider (Microsoft, Azure) 

Tutto questo avendo la possibilità di testare il tutto prima di effettuare lo spostamento: attraverso Test-clone capability, il tutto viene eseguito in un ambiente isolato (per non avere impatti sulle applicazioni in produzione)

Possibilità di migrare in batches (lotti), anche chiamati waves, usando VMs groups

    Fasi:
    1. Pianificare la migrazione in waves, ordine di migrazione ecc
    2. (Optional) Pre-migration test usando Test-clones
    3. Cutover to cloud (dal vecchio al nuovo), move VMs to GCE and migrate the application storage to Google Cloud
    4. Detach (da Migrate for Compute Engine)

# Migrate for Anthos e GKE

Per modernizzare apps passando da VMs a containers, presenti su GCP o fuori
- Vantaggi:
    - no vm layers (come Guest OS)
    - più efficienti e costi inferiori

- OS sorgenti delle VM supportati sono Linux o Windows
- Piattaforme di destinazione supportate:
    - Google Kubernetes Engine (GKE)
    - Anthos
    - Anthos clusters su VMWare
    - Anthos cluster su AWS ad esempio, quindi altri provider
    
Se le VMs sono fuori da GCP occorre:
1. Migrarle verso GCE tramite Migrate for Compute Engine
2. Migrare le GCE VMs in containers attraverso Migrate for Anthos e GKE


Note

N.B Per le immagini, il path qui presente utilizza il forwardslash, windows utilizza il backslash. Se non vengono visualizzate il problema potrebbe essere legato a quello