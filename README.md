<p align="center"><img src="ProgettoIs%20JustInTime/src/main/resources/static/images/logo.png" width="88" alt="JustInTime logo"></p>

<h1 align="center">JustInTime</h1>

<p align="center">A university team project: the full documentation of a turn-based card game for two to four players, and the Java application built from it.</p>

<p align="center"><b>English</b> · <a href="README.it.md">Italiano</a></p>

## About the project

JustInTime is a web game where players race against the clock. Each turn has a timer, every card you play can change how much time the next player has, and the first player to empty their hand wins. It was built by a four-person university team, from the requirements all the way to a working server-rendered Java application with accounts, matches, leaderboards and achievements.

> **The documentation is the main deliverable of this project.** The core of the work was writing it: analysing the problem, designing the system and the objects, planning the work and tracing requirements. The application is the implementation of that design, not the other way around. Start from the documents in [`Documentazione`](Documentazione) and read the code after.

This is a fork of the [original repository](https://github.com/LimeMoss/Progetto-JustInTime), kept public as a record of that coursework. It is an academic project, not a production game, and it is not presented as a solo project.

## The documentation

All documents are in [`Documentazione`](Documentazione) and are written in Italian.

| Document | Size | What it covers |
|---|---|---|
| [Statement of Work](Documentazione/Statement%20of%20work.pdf) | 12 pages | start and end dates, deliverables, functional and non-functional requirements |
| [Requirements Analysis Document (RAD)](Documentazione/RAD.pdf) | 65 pages | current and proposed system, functional requirements and non-functional ones (usability, reliability, performance, supportability, implementation, interfaces, operation, packaging, legal), scenarios, use case model, object model, dynamic model (activity, sequence and statechart diagrams), navigation paths and mock-ups |
| [System Design Document (SDD)](Documentazione/SDD.pdf) | 26 pages | decomposition into subsystems, persistent data management, access control and security, global software control, boundary conditions, services of each subsystem |
| [Object Design Document (ODD)](Documentazione/ODD.pdf) | 7 pages | the design patterns used, Bridge, Factory and State, each with the place where it appears in the project |
| [Traceability matrix](Documentazione/Testing_docs/Matrice%20di%20tracciabilit%C3%A0.xlsx) | spreadsheet | the traceability matrix, in `Testing_docs` |
| [Work log](Documentazione/Work%20done.xlsx) | spreadsheet | the record of the work done by the team |

A good reading order is the Statement of Work, then the RAD, the SDD and the ODD, and finally the code, where each pattern from the ODD can be found.

## How a match works

- The game supports two to four registered players.
- The deck has 60 cards. Each player starts with five, and one card is face up on the discard pile.
- On your turn you play a card whose value is one higher or one lower than the card on top of the discard pile, or a joker. If you have no valid card you draw one, and your future turns get one second shorter.
- Special cards can be played instead of a numbered card: **Accelera** takes two seconds off the next player's turn, **Rallenta** adds two seconds to the turn of the player who gets it, and **Jolly** counts as the top card plus one.
- A player whose time runs out is excluded, but the match goes on. The match ends when someone has no cards left, and the ranking follows the number of cards still in hand.

## Main features of the application

- registration, login, profile page and account editing or deletion;
- matches with a pre-match setup page, timed turns, turn order and special cards;
- a local leaderboard for each match and a global leaderboard;
- achievements unlocked by playing;
- a feedback form;
- a rules page and an end-of-match summary with the podium.

## Architecture

The application is a Spring Boot web project organised in layers. Controllers handle the routes and the session, services hold the game logic, Spring Data JPA repositories talk to MySQL, and Thymeleaf templates render the pages. The match itself lives in the model: a `Partita` owns the players and two decks (draw and discard, created through a factory), and its progress is handled by separate state classes for the start, the turns, the pause and the end of the game. The patterns are explained in the ODD.

## Run locally

The project targets Java 23, Maven and a local MySQL server. The `justintime` database is created on first start. The MySQL credentials are read from the `DB_USERNAME` (default `root`) and `DB_PASSWORD` environment variables, so set them before running.

```sh
export DB_PASSWORD="your-mysql-password"
cd "ProgettoIs JustInTime"
./mvnw spring-boot:run
```

Then open the address printed by Spring Boot, normally `http://localhost:8080`. The checked-in `target/` directory is a leftover of the original course repository; a clean build is preferable.

## Stack

Java 23 · Spring Boot 3.4 · Spring Web · Spring Data JPA / Hibernate · Thymeleaf · MySQL · Maven · HTML · CSS · JavaScript

## Team

The original repository is owned by [@LimeMoss](https://github.com/LimeMoss). The team also includes [@Ferdinando980](https://github.com/Ferdinando980), [@Vincy1212](https://github.com/Vincy1212) and [@YuliaD26](https://github.com/YuliaD26). Each contributor's commits are preserved in the history.

## Academic context

Developed as a university team project. The course deliverables are the documents listed above, and the code is a snapshot of the work as it was at the end of the course, not a rewritten portfolio demo.

## License

The original repository does not declare a license, so all rights remain with its authors. The source is visible for academic and portfolio evaluation only.
