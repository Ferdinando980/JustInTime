<p align="center"><img src="ProgettoIs%20JustInTime/src/main/resources/static/images/logo.png" width="88" alt="Logo di JustInTime"></p>

<h1 align="center">JustInTime</h1>

<p align="center">Un gioco di carte a turni per due-quattro giocatori, sviluppato come progetto universitario di gruppo.</p>

<p align="center"><a href="README.md">English</a> · <b>Italiano</b></p>

## Il progetto

JustInTime è un gioco web in cui si gioca contro il tempo. Ogni turno ha un timer, ogni carta giocata può cambiare il tempo del giocatore successivo e vince chi resta per primo senza carte in mano. L'ha realizzato un gruppo universitario di quattro persone, dai documenti dei requisiti fino a un'applicazione Java funzionante, con account, partite, classifiche e obiettivi.

Questo è un fork del [repository originale](https://github.com/LimeMoss/Progetto-JustInTime), reso pubblico come testimonianza del lavoro svolto. È un progetto accademico, non un gioco in produzione, e non è presentato come lavoro individuale.

## Come funziona una partita

- Il gioco prevede da due a quattro giocatori registrati.
- Il mazzo ha 60 carte. Ogni giocatore parte con cinque carte e al centro c'è una carta scoperta nel mazzo di scarto.
- Nel proprio turno si gioca una carta di valore superiore o inferiore di uno rispetto a quella in cima agli scarti, oppure un jolly. Se non ce ne sono si pesca una carta, e i turni successivi durano un secondo in meno.
- Le carte speciali si giocano al posto di una numerata: **Accelera** toglie due secondi al turno del giocatore successivo, **Rallenta** aggiunge due secondi al turno di chi la ottiene, **Jolly** vale la carta in cima più uno.
- Chi finisce il tempo viene escluso, ma la partita continua. La partita finisce quando qualcuno resta senza carte e la classifica segue il numero di carte rimaste in mano.

## Funzioni principali

- registrazione, accesso, pagina del profilo e modifica o eliminazione dell'account;
- partite con una pagina di preparazione, turni a tempo, ordine di gioco e carte speciali;
- una classifica locale per ogni partita e una classifica globale;
- obiettivi che si sbloccano giocando;
- un modulo per i feedback;
- una pagina con il regolamento e un riepilogo di fine partita con il podio.

## Architettura

L'applicazione è un progetto web Spring Boot organizzato a livelli. I controller gestiscono le rotte e la sessione, i servizi contengono la logica di gioco, i repository Spring Data JPA parlano con MySQL e i template Thymeleaf generano le pagine. La partita vive nel modello: una `Partita` possiede i giocatori e due mazzi (pesca e scarto, creati tramite una factory), e il suo andamento è gestito da classi di stato separate per l'avvio, i turni, la pausa e la fine del gioco.

La documentazione di progetto è nella cartella `Documentazione`: documento di analisi dei requisiti (RAD), di progettazione del sistema (SDD) e degli oggetti (ODD), statement of work, un registro del lavoro svolto e una matrice di tracciabilità.

## Avvio in locale

Il progetto richiede Java 23, Maven e un server MySQL in locale. Il database `justintime` viene creato al primo avvio; prima di eseguire imposta il tuo utente e la tua password MySQL in `src/main/resources/application.properties`.

```sh
cd "ProgettoIs JustInTime"
./mvnw spring-boot:run
```

Poi si apre l'indirizzo stampato da Spring Boot, di norma `http://localhost:8080`. La cartella `target/` inclusa nel repository è un residuo del progetto originale: meglio una compilazione pulita.

## Tecnologie

Java 23 · Spring Boot 3.4 · Spring Web · Spring Data JPA / Hibernate · Thymeleaf · MySQL · Maven · HTML · CSS · JavaScript

## Gruppo

Il repository originale appartiene a [@LimeMoss](https://github.com/LimeMoss). Del gruppo fanno parte anche [@Ferdinando980](https://github.com/Ferdinando980), [@Vincy1212](https://github.com/Vincy1212) e [@YuliaD26](https://github.com/YuliaD26). I commit di ciascuno sono conservati nella cronologia.

## Contesto accademico

Sviluppato come progetto universitario di gruppo. I documenti consegnati per il corso sono in `Documentazione`, e il codice è una fotografia del lavoro com'era a fine corso, non una demo riscritta per il portfolio.

## Licenza

Il repository originale non dichiara una licenza, quindi tutti i diritti restano ai suoi autori. Il codice è visibile solo per valutazione accademica e di portfolio.
