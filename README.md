# Draw-It-or-Lose-It-Web-Game


```markdown
# Draw It or Lose It – Web Game (CS 230 Project One)

![image](https://github.com/user-attachments/assets/be8fd8fb-43e2-43d8-af9a-e23085fbdb0b)
![image](https://github.com/user-attachments/assets/be8fd8fb-43e2-43d8-af9a-e23085fbdb0b)

> A multi-platform, web-based re-imagining of *Draw It or Lose It*, built for **The Gaming Room** by **Creative Technology Solutions (CTS)**.

---

## 📜 Executive Summary
This repository contains the first working prototype and supporting design documents for migrating *Draw It or Lose It* from a single-platform Android app to a distributed, browser-accessible game.  
Key goals:

- **Single-Instance Game Service** – guarantee one live game in memory via the *Singleton* pattern.  
- **Unique Names** – prevent duplicate game, team, or player names using the *Iterator* pattern.  
- **Extensible Domain Model** – share common fields (`id`, `name`) through a base `Entity` class.

---

## ✨ Features
| Requirement | Implementation |
|-------------|----------------|
| Multiple teams per game | `Game` holds a `List<Team>` |
| Multiple players per team | `Team` holds a `List<Player>` |
| Unique names & IDs | Checked in `GameService.add*()` |
| One service instance only | Private constructor & static `getInstance()` |
| Future-proof web deployment | Clean separation of model / service / driver layers |

---

## 🏗️ Tech Stack
- **Language:** Java 17
- **Build:** Eclipse 2023-09 (or any Gradle/Maven IDE)
- **Testing:** JUnit 5 (starter tests included)
- **Documentation:** UML class diagram (`/docs/DrawItOrLoseIt_UML.png`)

---

## 🔎 Design Patterns Used
| Pattern | Class(es) | Purpose |
|---------|-----------|---------|
| Singleton | `GameService` | Ensure only one game controller lives in memory |
| Iterator | `GameService.addGame/getGame` & `addTeam/addPlayer` | Traverse existing objects to enforce name uniqueness |
| Inheritance | `Entity` → `Game`, `Team`, `Player` | Share common identity fields & behaviour |

---

## 🌳 Project Structure
```

.
├── README.md
├── docs/
│   └── DrawItOrLoseIt\_UML.png
└── src/
├── main/java/com/cts/drawit/
│   ├── model/
│   │   ├── Entity.java
│   │   ├── Game.java
│   │   ├── Team.java
│   │   └── Player.java
│   ├── service/
│   │   └── GameService.java
│   └── ProgramDriver.java
└── test/java/com/cts/drawit/
└── GameServiceTest.java

````

---

## 🚀 Getting Started

1. **Clone the repo**
   ```bash
   git clone https://github.com/YourOrg/draw-it-or-lose-it.git
   cd draw-it-or-lose-it
````

2. **Import into Eclipse**
   *File → Import → Existing Gradle Project* (or *Maven* if you converted the build).
3. **Run the driver**
   `ProgramDriver` contains a `main()` with sample data. Hit ▶️ to verify console output.

---

## 🧪 Running Tests

```bash
./gradlew test     # or: mvn test
```

Unit tests cover singleton instantiation and uniqueness constraints.

---

## 📐 UML

See `/docs/DrawItOrLoseIt_UML.png` for the full domain model. It highlights:

* Association between `Game` ↔ `Team` ↔ `Player`
* Inheritance from `Entity`
* Static factories in `GameService`

---

## 🌍 Deployment Next Steps

| Layer            | Milestone                       | Notes                                        |
| ---------------- | ------------------------------- | -------------------------------------------- |
| **Presentation** | React / Thymeleaf web UI        | Consume REST API                             |
| **Service**      | Spring Boot REST controllers    | Expose `GameService` methods                 |
| **Persistence**  | JPA / Hibernate                 | Store entities in SQL                        |
| **Hosting**      | AWS Elastic Beanstalk or Heroku | Meets client “serve multiple platforms” goal |

---


## 📄 License

Distributed under the MIT License – see `LICENSE` file for details.

---


