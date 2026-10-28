<p align="center"><img src="ProgettoIs%20JustInTime/src/main/resources/static/images/logo.png" width="88" alt="Logo di JustInTime"></p>

<h1 align="center">JustInTime</h1>

<p align="center">Un progetto universitario di gruppo: la documentazione completa di un gioco di carte a turni per due-quattro giocatori e l'applicazione Java realizzata a partire da essa.</p>

<p align="center"><a href="README.md">English</a> · <b>Italiano</b></p>

## Il progetto

JustInTime è un gioco web in cui si gioca contro il tempo. Ogni turno ha un timer, ogni carta giocata può cambiare il tempo del giocatore successivo e vince chi resta per primo senza carte in mano. L'ha realizzato un gruppo universitario di quattro persone, dai requisiti fino a un'applicazione Java funzionante, con account, partite, classifiche e obiettivi.

> **La documentazione è la parte più importante del progetto.** Il cuore del lavoro è stato scriverla: analizzare il problema, progettare il sistema e gli oggetti, pianificare il lavoro e tracciare i requisiti. L'applicazione è l'implementazione di quel progetto, non il contrario. Conviene partire dai documenti nella cartella [`Documentazione`](Documentazione) e leggere il codice dopo.

Questo è un fork del [repository originale](https://github.com/LimeMoss/Progetto-JustInTime), reso pubblico come testimonianza del lavoro svolto. È un progetto accademico, non un gioco in produzione, e non è presentato come lavoro individuale.

## La documentazione

Tutti i documenti sono nella cartella [`Documentazione`](Documentazione) e sono scritti in italiano.

| Documento | Dimensione | Che cosa contiene |
|---|---|---|
| [Statement of Work](Documentazione/Statement%20of%20work.pdf) | 12 pagine | date di inizio e fine, consegne, requisiti funzionali e non funzionali |
| [Requirements Analysis Document (RAD)](Documentazione/RAD.pdf) | 65 pagine | sistema attuale e proposto, requisiti funzionali e non funzionali (usabilità, affidabilità, prestazioni, supportabilità, implementazione, interfacce, operation, packaging, aspetti legali), scenari, modello dei casi d'uso, modello a oggetti, modello dinamico (activity, sequence e statechart diagram), percorsi di navigazione e mock-up |
| [System Design Document (SDD)](Documentazione/SDD.pdf) | 26 pagine | decomposizione in sottosistemi, gestione dei dati persistenti, controllo degli accessi e sicurezza, controllo globale del software, condizioni limite, servizi di ogni sottosistema |
| [Object Design Document (ODD)](Documentazione/ODD.pdf) | 7 pagine | i design pattern usati, Bridge, Factory e State, ciascuno con il punto in cui compare nel progetto |
| [Matrice di tracciabilità](Documentazione/Testing_docs/Matrice%20di%20tracciabilit%C3%A0.xlsx) | foglio di calcolo | la matrice di tracciabilità, in `Testing_docs` |
| [Registro del lavoro](Documentazione/Work%20done.xlsx) | foglio di calcolo | il resoconto del lavoro svolto dal gruppo |

Un buon ordine di lettura è lo Statement of Work, poi RAD, SDD e ODD, e infine il codice, dove si ritrova ciascun pattern descritto nell'ODD.

## Come funziona una partita

- Il gioco prevede da due a quattro giocatori registrati.
- Il mazzo ha 60 carte. Ogni giocatore parte con cinque carte e al centro c'è una carta scoperta nel mazzo di scarto.
- Nel proprio turno si gioca una carta di valore superiore o inferiore di uno rispetto a quella in cima agli scarti, oppure un jolly. Se non ce ne sono si pesca una carta, e i turni successivi durano un secondo in meno.
- Le carte speciali si giocano al posto di una numerata: **Accelera** toglie due secondi al turno del giocatore successivo, **Rallenta** aggiunge due secondi al turno di chi la ottiene, **Jolly** vale la carta in cima più uno.
- Chi finisce il tempo viene escluso, ma la partita continua. La partita finisce quando qualcuno resta senza carte e la classifica segue il numero di carte rimaste in mano.

## Funzioni principali dell'applicazione

- registrazione, accesso, pagina del profilo e modifica o eliminazione dell'account;
- partite con una pagina di preparazione, turni a tempo, ordine di gioco e carte speciali;
- una classifica locale per ogni partita e una classifica globale;
- obiettivi che si sbloccano giocando;
- un modulo per i feedback;
- una pagina con il regolamento e un riepilogo di fine partita con il podio.

## Architettura

L'applicazione è un progetto web Spring Boot organizzato a livelli. I controller gestiscono le rotte e la sessione, i servizi contengono la logica di gioco, i repository Spring Data JPA parlano con MySQL e i template Thymeleaf generano le pagine. La partita vive nel modello: una `Partita` possiede i giocatori e due mazzi (pesca e scarto, creati tramite una factory), e il suo andamento è gestito da classi di stato separate per l'avvio, i turni, la pausa e la fine del gioco. I pattern sono spiegati nell'ODD.

## Avvio in locale

Il progetto richiede Java 23, Maven e un server MySQL in locale. Il database `justintime` viene creato al primo avvio. Le credenziali MySQL si leggono dalle variabili d'ambiente `DB_USERNAME` (predefinito `root`) e `DB_PASSWORD`, quindi vanno impostate prima di eseguire.

```sh
export DB_PASSWORD="la-tua-password-mysql"
cd "ProgettoIs JustInTime"
./mvnw spring-boot:run
```

Poi si apre l'indirizzo stampato da Spring Boot, di norma `http://localhost:8080`. La cartella `target/` inclusa nel repository è un residuo del progetto originale: meglio una compilazione pulita.

## Tecnologie

Java 23 · Spring Boot 3.4 · Spring Web · Spring Data JPA / Hibernate · Thymeleaf · MySQL · Maven · HTML · CSS · JavaScript

## Gruppo

Il repository originale appartiene a [@LimeMoss](https://github.com/LimeMoss). Del gruppo fanno parte anche [@Ferdinando980](https://github.com/Ferdinando980), [@Vincy1212](https://github.com/Vincy1212) e [@YuliaD26](https://github.com/YuliaD26). I commit di ciascuno sono conservati nella cronologia.

## Contesto accademico

Sviluppato come progetto universitario di gruppo. Le consegne del corso sono i documenti elencati sopra, e il codice è una fotografia del lavoro com'era a fine corso, non una demo riscritta per il portfolio.

## Licenza

Il repository originale non dichiara una licenza, quindi tutti i diritti restano ai suoi autori. Il codice è visibile solo per valutazione accademica e di portfolio.
