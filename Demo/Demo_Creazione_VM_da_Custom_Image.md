# Custom Image
[Crea custom image](https://cloud.google.com/compute/docs/images/create-custom)

Obiettivo: Creare una Custom Image, da questa creare un'istanza di VM o Instance Template

Partendo da un disco associato ad una VM esistente, su di esso vi è il suo OS, vado a creare una **Custom Image**

*COMPUTE ENGINE -> STORAGE -> DISKS-> CREA IMAGE*

Nel form di creazione della Custom image specifico alcuni campi tra cui, la location, il luogo in cui verranno create le VMs. 

N.B

*Stoppare la VM, per poter utilizzare il suo disco associato. Occorre farlo prima altrimenti questo stop non viene rilevato da GCP.*

A partire da questa Custom Image creata posso adesso creare direttamente un'istanza di VM. 

*~~VM~~-> IMAGE -> VMs*

(~~VM~~ Cancello la VM al termine)

Posso farlo anche indirettamente, tramite un instance template e collegare il boot disk alla custom image creata.

*~~VM~~ -> IMAGE -> INSTANCE TEMPLATE -> VMs*


Ricorda di cambiare gli script associati, l'immagine ha già il sw scaricato. 
Usare l'immagine implica una riduzione del tempo di boot, sull'immagine scarico il sw necessario per le successive VMs
