# Note about the presentation

**Maximum Duration**: 10 minutes
**Slides**: 10 slides
**Pacing**: 1 minute per slide

## Slide 0 titolo

## Slide 1: Introduction & Problem Statement
- **Title**: "Dallo studio Precedente ..."
- Brief overview of the research problem
- Why location privacy matters in IoT and mobile applications
- Research objectives and contributions


Possiamo incominciare presentando \[HE LA-MQTT\] per poi passare al macro argomento di Req/res vs Pub/Sub
Ovviamente la privacy è un tema centrale, oggi che ci fidiamo sempre più ciecamente dei provider di servizi
Tra gli obbiettivi della ricerca, abbiamo
- Analizzare la differenza fra i protocolli di comunicazione in ambienti omomorficamente cifrati
- Proporre un personale protocollo che sia coerente con lo studio

## Slide 2: Background - Communication Protocols
- **Request-Response vs Publish-Subscribe**
- HTTP/CoAP for IoT devices
    - HTTP: protocollo sincrono, client-server model, CoAP ancora più leggero
- MQTT and LA-MQTT for real-time communication
    - MQTT: leggero, publish-subscribe model, ottimo per IoT, in chiaroooo
    - LA-MQTT: ottimizzato per ambienti in cui la geolocalizzazione è fondamentale
- Come scegliere uno dei due?
    - contesto di utilizzo:
        - HTTP/CoAP: quando la richiesta di dati è sporadica e non richiede aggiornamenti in tempo reale
        - MQTT/LA-MQTT: quando i dati devono essere aggiornati frequentemente e in tempo reale, come nelle applicazioni. Il server SA quando gli utenti devono ricevere gli aggiornamenti, allerta privacy.


## Slide 3: Location Referencing & Space-Filling Curves
- **Universal Location Referencing techniques**
- Distance measures between vectors
- Cantor Pairing for coordinate mapping
- Z-order curves for spatial indexing
- Benefits for location-based matching

Prima di tutto, analizziamo lo studio delle rappresentazioni geografiche in computer.

## Slide 4: Privacy-Preserving Techniques
- **Homomorphic Encryption (HE) fundamentals**
- Types: Partial (PHE) vs Fully Homomorphic (FHE)
- HE Translation Keys
- Proxy re-encryption

Il tema pricipale di questo studio è proprio ... Commentare i due tipi principali.
Esempio di Chiave di traduzione e Proxy re-encryption per salvare i dati come in tesi.

## Slide 5: System Architecture Overview
- Image of **System components and actors**
- Location Data Sources
- Mobile Clients
- Server infrastructure
- Certification Authority/Proxy
- Worker nodes

Descrivere brevemente

## Slide 6: Protocol Flow & Security Model
- **Step-by-step protocol execution**

Riassunto del workflow:
1. LDs and MCs ottengono le impostazioni del sistema dal server. LDs ottiene la chiave privata dalla CA, mentre MCs la genera e manda la chiave pubblica alla stessa.
2. LDs collect data and send crypted to the server.
3. MC pubblica la propria posizione cifrata al server sotto **propria chiave pubblica**
4. Il server chiede alla ca le chiavi di traduzione e cambia la chiave di encryption dei dati
5. Il lavoro passa ai worker nodes che si occupano di calcolare le distanze e rispondere al client.
6. Il server risponde al client con i risultati, che sono i possibili matching degli LDs.


## Slide 7: Threat Model
- Malicious actors
    - Workers -> fake workload
    - Server -> Multiple backups
    - Network -> traffico cifrato HE
    - Client -> firma digitale al momento dell'accesso


## Slide 8: Esempio di attacco

Impersonificare un client HE LA-MQTT, con una ricerca binaria in piu' dimensioni trovo le aree a cui si è sotto-scritto e se sono state pubblicate le coordinate, posso fare un attacco di tipo "brute force" per trovare le coordinate del client.

Tramite API:

## Slide 9: Analisi sicurezza
abbastanza guidata.

Focalizzarsi sulle considerazioni in caso CA venga compromessa.

## Slide 10: Risultati 1: cifrare e decriptare i dati
linearmente più lento rispetto a un blob unico con RSA.

## Slide 11: Risultati 2: tempo totale
spike dovute a un rumore randomico, ma in generale il tempo di risposta è accettabile per un sistema di questo tipo, ovviamente più lento come previsto.

## Slide 12: Conclusion & Future Work
- **Summary of contributions**
- Protocol scalability insights
- Limitations and areas for improvement
- Future research directions and potential enhancements

