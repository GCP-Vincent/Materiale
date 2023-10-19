# Panoramica su Compute Engine, Instance Groups e Load Balancing

- [Compute Engine](#compute-engine)
- [Instance Groups](#instance-groups) 
- [Load Balancing](#load-balancing)

# Compute Engine Service 
 
- Servizio che consente di creare e gestire macchine virtuali in GCP

- Consente di gestire auto scaling, per aumentare/diminuire il numero di instanze

- Consente di gestire il load balancing, quindi distribuire il carico

- Consente di collegarsi allo storage


### Demo
Obiettivo
Su GCP avviare una virtual machine tramite Compute Engine
Dopo averla avviata e smanettato un po' installando apache, vediamo che l'indirizzo IP interno (privato), non cambia se cambia lo stato della VM (stop, run). Se invece stoppo e faccio ripartire la VM quello esterno (pubblico) cambia.

IMPORTANTE

L'indirizzo esterno (pubblico) di default è infatti effimero, viene quindi riassegnato ad ogni modifica dello stato della VM.
Per averne uno fisso, occorre crearlo e collegarlo. **Static IP Address**. Anche quando non lo utilizzo lo pago. Anche se il nome può ingannare questo è pubblico, da non confondere con l'indirizzo statico privato

## STARTUP SCRIPT - INSTANCE TEMPLATE - CUSTOM IMAGE

Ho diverse opzioni per creare un'instanza di una VM e settere atumaticamente delle configurazioni.  

**Startuo script**: Nella creazione di un'istanza di VM, tramite Compute Engine, si va a definire nel campo che trovo in, MANAGEMENT-> SECURITY -> DISKS -> NETWORKING -> SOLE TENANCY, (potrebbe cambiare col tempo il front-end), definisco lo script che voglio fare eseguire al bootstrap (Automation di Management) 


Note

N.B Per le immagini, il path qui presente utilizza il forwardslash /, windows utilizza il backslash \ . Se non vengono visualizzate il problema potrebbe essere legato a quello 