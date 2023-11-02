# Creazione MIG

Un pool di instanze di VMs identiche

- **Instance template** obbligatorio (base di partenza)
- Configurazione **auto scaling** 
    - Definendo minimum number di instanze
    - Definendo maximum number di instanze
    - Definire delle autoscaling metrics (utilizzo cpu, load balancer, altre metriche definite da Stack Driver di Google Cloud)

- E' possibile definire inoltre:
    - Cool-down period: periodo prima di rivedere le metriche, considerare la macchina
    - Scale-In controls: per evitare un calo drastrico delle istanze (ad es. non scalare più di tot istanze in 5 minuti). 
    - Auto healing: configurare degli *health checks* (oggetti in GCP) con un *initial delay* (tempo di attesa prima della loro verifica). In base a questi oggetti si controlla lo stato di salute dell'istanza

**Creazione da portale di MIG con autoscaling e autohealing**

Dalla sezione **Compute Engine**, creare **Instance Template** (obbligatorio). Dopo averlo creato, sempre nella sezione di Compute Engine ho una parte legata a **Instance Groups** (Managed o Unmanaged), ne creo uno da zero.

Nella scelta MIG, in questo caso, ho due possibilità:
-   MIG **stateless** (per Web application o REST API)      
-   MIG **stateful** (adatto per persistent data o configurazioni, preservare lo stato della VM: nome, persistent disk collegati e metadati)

Scelto ad esempio stateless, gli do un nome, una descrizione, indico l'instance template da cui creare le VMs, definisco la location, definisco l'autoscaling mode (on: add o remove, scale out: solo aggiunta, off: disabilitato), definisco il numero e le metriche da usare. Definisco il Cool-down period e il controllo sullo scale-in (decrementa il numero di istanze quando il traffico cala).

Successivamente segue la parte legata all'auto-healing, qui vanno definiti gli health check, indicando come controllare, ogni quanto, quanto tempo aspettare la risposta e le relative soglie di salute (quanti successi consecutivi per dire è in salute, quanti insuccessi consecutivi per ritenerla non buona).

Una volta creato, definisco l'initial delay, ovvero il tempo di ritardo prima di far partire il primo check di salute dopo il riavvio.

Creato il MIG stateless è possibile poi editarlo
