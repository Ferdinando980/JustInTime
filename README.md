<p align="center"><img src="ProgettoIs%20JustInTime/src/main/resources/static/images/logo.png" width="88" alt="JustInTime logo"></p>

<h1 align="center">JustInTime</h1>

<p align="center">A turn-based card game for two to four players, developed as a university team project.</p>

<p align="center"><b>English</b> · <a href="README.it.md">Italiano</a></p>

## About the project

JustInTime is a web game where players race against the clock. Each turn has a timer, every card you play can change how much time the next player has, and the first player to empty their hand wins. It was built by a four-person university team, from the requirements documents to a working server-rendered Java application with accounts, matches, leaderboards and achievements.

This is a fork of the [original repository](https://github.com/LimeMoss/Progetto-JustInTime), kept public as a record of that coursework. It is an academic project, not a production game, and it is not presented as a solo project.

## How a match works

- The game supports two to four registered players.
- The deck has 60 cards. Each player starts with five, and one card is face up on the discard pile.
- On your turn you play a card whose value is one higher or one lower than the card on top of the discard pile, or a joker. If you have no valid card you draw one, and your future turns get one second shorter.
- Special cards can be played instead of a numbered card: **Accelera** takes two seconds off the next player's turn, **Rallenta** adds two seconds to the turn of the player who gets it, and **Jolly** counts as the top card plus one.
- A player whose time runs out is excluded, but the match goes on. The match ends when someone has no cards left, and the ranking follows the number of cards still in hand.

## Main features

- registration, login, profile page and account editing or deletion;
- matches with a pre-match setup page, timed turns, turn order and special cards;
- a local leaderboard for each match and a global leaderboard;
- achievements unlocked by playing;
- a feedback form;
- a rules page and an end-of-match summary with the podium.

## Architecture

The application is a Spring Boot web project organised in layers. Controllers handle the routes and the session, services hold the game logic, Spring Data JPA repositories talk to MySQL, and Thymeleaf templates render the pages. The match itself lives in the model: a `Partita` owns the players and two decks (draw and discard, created through a factory), and its progress is handled by separate state classes for the start, the turns, the pause and the end of the game.

The project documentation is in the `Documentazione` folder: requirements analysis document (RAD), system design document (SDD), object design document (ODD), statement of work, a work log and a traceability matrix.

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

Developed as a university team project. The course deliverables are included in `Documentazione`, and the code is a snapshot of the work as it was at the end of the course, not a rewritten portfolio demo.

## License

The original repository does not declare a license, so all rights remain with its authors. The source is visible for academic and portfolio evaluation only.
