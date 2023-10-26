# Google Cloud Pub/Sub

Ricerco il servizio Pub/Sub

Procedo con la creazione di un Topic (in cui vengono depositati i messaggi), gli assegno un nome.

Successivamente creo diverse Subscriptions, indicando il nome, il tipo di delivery (pull o push), se abilitare la retention dei messaggi (non confermati e confermati), determinare o meno la scadenza per la subscription (expiration), l'ack deadline (in termini di secondi, finestra di tempo che ha il subscriber per confermare il processamento del messaggio e toglierlo dalla coda della subscription). Altre opzioni riguardano un topic diverso (dead lettering), e policy di re-invio.

Una volta create, sempre nella sezione Topics, posso pubblicare dei messaggi. In questo caso simulo un messaggio non definito da un publisher. Posizionandomi nelle diverse subscriptions, facendo pull (se delivery type è pull), ricevo i messaggi creati.

Occorre abilitare l'ACK dei messaggi, per confermare la ricezione e processamento dei messaggi al topic. Una volta indicato come ack, viene eliminato dalla coda della sottoscrizione.  

E' possibile creare uno snapshot, dello stato di una specifica subscription (quindi stato dei messaggi nella coda della subscription). Esistono poi delle versioni lite, meno costose, ma meno ridondate. 