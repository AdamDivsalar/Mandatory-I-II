# Mandatory II - Læringsmål

**Adam Leon Divsalar**
Teknologi 2. semester datamatiker, KEA

Her har jeg skrevet alle læringsmål fra "Learning Goals"-kolonnen i semesterplanen.
Ved "can"-mål viser jeg et eksempel og skriver "Det kan jeg". Ved "knows/understands"
skriver jeg stikord, jeg kan forklare mundtligt ud fra. Jeg dækker uge 1, 2, 3, 5, 6, 7, 8 og 9.

---

## Uge 1 - Terminal og Git

**Can navigate the terminal: ls, cd, whoami, pwd.**

```bash
pwd            # viser stien til den mappe jeg står i
ls -la         # lister alt, også skjulte filer
cd projects    # går ned i en mappe
cd ..          # går et niveau op
whoami         # viser mit brugernavn
```

Det kan jeg!

**Can create, delete files / folders: mkdir, rm, cp, mv, touch, nano.**

```bash
mkdir test          # opret mappe
touch file.txt      # opret tom fil
nano file.txt       # åbn fil i terminal-editoren
cp file.txt copy.txt    # kopier fil
mv copy.txt navn.txt    # omdøb/flyt fil
rm file.txt         # slet fil
rm -r test          # slet mappe og alt indhold
```

Det kan jeg!

**Can use the following basic terminal commands: cat, wc, uniq, sort.**

```bash
cat file.txt        # printer hele filen
wc -l file.txt      # tæller linjer
sort navne.txt      # sorterer alfabetisk
sort navne.txt | uniq   # fjerner gentagne linjer der står ved siden af hinanden
```

`uniq` fjerner kun ens linjer der står lige efter hinanden, så jeg sorterer altid først.

Det kan jeg!

**Can create a new repository in your prefered Git provider.**

Jeg går ind på GitHub, klikker "New repository", giver den et navn og klikker "Create repository".
Derefter kobler jeg en lokal mappe på:

```bash
git init
git remote add origin git@github.com:brugernavn/giftr.git
git branch -M main
git push -u origin main
```

Det kan jeg!

**Can perform basic Git operations: clone, add, commit, push, pull.**

```bash
git clone <repo-url>      # hent repository ned
git add .                # stage mine ændringer
git commit -m "besked"   # gem lokalt
git push                 # send op til remote
git pull                 # hent og merge det nyeste ned
```

Det kan jeg!

---

## Uge 2 - Hardware, Software, Talsystemer, Encoding

**Can list the main hardware components of a computer, their functions and the Von Neumann architecture.**

Hovedkomponenter:

- CPU - udfører instruktionerne, det er computerens hjerne. Den indeholder ALU'en
  (regning), control unit (styring) og registre (midlertidig lagring).
- RAM - hurtig, flygtig hukommelse til det program der kører lige nu. Den tømmes når der slukkes.
- Lagring (SSD/HDD) - permanent lagring der bliver liggende.
- Bundkort og bus - binder komponenterne sammen og flytter data rundt.
- I/O - input (tastatur, mus) og output (skærm, printer).

Von Neumann-arkitektur:

- Kode og data ligger i den samme hukommelse.
- CPU'en kører en fast cyklus: fetch -> decode -> execute.
- Flaskehalsen er at data og instruktioner deler den samme bus til RAM.

**Can explain how computers work, starting from hardware all the way to software.**

Jeg tænker på computeren i lag:

- Hardware - de fysiske dele (CPU, RAM, disk).
- Operativsystem - styrer hardwaren og giver services (Windows, Linux).
- Programmer og apps - det jeg som bruger faktisk bruger (fx Giftr).
- Brugerinput - det jeg gør, der sætter handlinger i gang.

Flow: jeg klikker på en knap -> OS'et modtager mit input -> programmet sender instruktioner ->
CPU'en behandler dem -> resultatet vises på skærmen.

**Can talk about processes in operating systems.**

- En proces er et program der kører.
- Hver proces har sin egen hukommelse og sin egen tilstand (running, waiting, terminated).
- OS'et styrer processerne med scheduling (hvem kører nu) og context switching (skift mellem dem).
- Det er det der giver multitasking, så flere programmer kører "samtidig".
- En proces kan have flere tråde, der deler procesens hukommelse.

**Can talk about different number representations: Binary, Hexadecimal, Decimal.**

- Binær (base 2): kun 0 og 1. Det er det computeren regner i. Eksempel: 1101 = 13.
- Decimal (base 10): cifrene 0-9. Det er det vi mennesker bruger til hverdag.
- Hexadecimal (base 16): 0-9 og A-F. En kompakt måde at skrive binær på. Eksempel: D = 13.

```
Decimal:      13
Binær:        1101    (8 + 4 + 0 + 1)
Hexadecimal:  D
```

Det kan jeg, og jeg kan regne frem og tilbage i hånden.

**Can bring up real-world use cases for different number representations.**

- Binær: inde i selve hardwaren (logiske kredsløb, hukommelse).
- Decimal: brugerflader og almindelig regning, fx priser i Giftr.
- Hex: farvekoder i web (#FF0000 er rød), hukommelsesadresser, MAC-adresser og debugging.

Det kan jeg!

**Can explain different charsets like ASCII and Unicode and how they differ.**

- ASCII: bruger 7 bit, altså 128 tegn. Den dækker engelske bogstaver, tal og symboler, men ikke æ, ø og å. Eksempel: A = 65.
- Unicode: dækker stort set alle sprog og symboler, også emojis. Den lagres typisk som UTF-8.
- Forskellen er at ASCII er begrænset, mens Unicode er universel og bagudkompatibel med ASCII.

Det er præcis derfor jeg satte `DEFAULT CHARACTER SET utf8` på databasen i Mandatory I.
Ellers bliver de danske tegn ødelagt.

---

## Uge 3 - Databaser og intro til SQL

**Knows about different types of databases and their use cases.**

Relationelle databaser (SQL):

- Eksempel: MySQL.
- Data ligger i tabeller (rækker og kolonner), med faste skemaer og relationer via nøgler.
- Bruges til struktureret data, banksystemer og web-apps (fx Giftr).

NoSQL-databaser:

- Eksempel: MongoDB (dokumenter), Redis (key-value), Neo4j (graf).
- Fleksibel struktur, ofte JSON-lignende dokumenter.
- Bruges til store skalerbare apps og løst struktureret data.

Min tommelfingerregel: jeg vælger relationelt når relationer og konsistens er vigtigt,
og NoSQL når fleksibilitet og skalering vejer tungest.

**Can setup a new MySQL database and connect to it.**

```sql
CREATE DATABASE giftr DEFAULT CHARACTER SET utf8;
USE giftr;
```

```bash
mysql -u root -p
```

Det kan jeg!

**Can create DDL statements to create tables.**

```sql
CREATE TABLE users (
    id    INT AUTO_INCREMENT PRIMARY KEY,
    name  VARCHAR(100),
    email VARCHAR(100)
);
```

DDL står for Data Definition Language (CREATE, ALTER, DROP).

Det kan jeg!

**Can create DML (SELECT, INSERT) statements.**

```sql
INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');
SELECT * FROM users;
```

DML står for Data Manipulation Language (SELECT, INSERT, UPDATE, DELETE).

Det kan jeg!

**Can use WHERE clause to filter results.**

```sql
SELECT * FROM users WHERE name = 'Alice';
```

Det kan jeg!

---

## Uge 5 - SQL II (nøgler, aggregater, joins, PRs)

**Can define Primary Keys.**

- En primærnøgle identificerer hver række entydigt.
- Den skal være unik og NOT NULL.

```sql
CREATE TABLE users (
    id   INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100)
);
```

Det kan jeg!

**Understands how Foreign Keys work.**

- En fremmednøgle binder en tabel til en anden.
- Den sikrer referentiel integritet, så jeg kun kan pege på data der rent faktisk findes.

```sql
CREATE TABLE orders (
    id      INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

Her skal værdien i `orders.user_id` findes i `users.id`.

**In SELECT statements, can use (with moderate help):**

LIMIT, ORDER BY, GROUP BY:

```sql
SELECT * FROM users LIMIT 5;
SELECT * FROM users ORDER BY name ASC;
SELECT user_id, COUNT(*) FROM orders GROUP BY user_id;
```

Aggregatfunktioner (COUNT, SUM, AVG, MIN, MAX):

```sql
SELECT COUNT(*) FROM users;
SELECT AVG(price) FROM products;
SELECT MIN(price), MAX(price) FROM products;
```

Pattern matching med LIKE og wildcards (% er mange tegn, _ er ét tegn):

```sql
SELECT * FROM users WHERE name LIKE 'A%';        -- starter med A
SELECT * FROM users WHERE email LIKE '%@gmail.com';
```

JOIN til at samle data fra flere tabeller:

```sql
SELECT users.name, orders.id
FROM users
JOIN orders ON users.id = orders.user_id;
```

Det kan jeg, og jeg brugte dem alle i Mandatory I.

**Can create inner, left and right joins after looking up the syntax.**

```sql
-- INNER: kun rækker med match i begge tabeller
SELECT * FROM users INNER JOIN orders ON users.id = orders.user_id;

-- LEFT: alle users, også dem uden orders
SELECT * FROM users LEFT JOIN orders ON users.id = orders.user_id;

-- RIGHT: alle orders, også dem uden user
SELECT * FROM users RIGHT JOIN orders ON users.id = orders.user_id;
```

Det kan jeg!

**Can create DDL statements to create tables with constraints: PRIMARY KEY, AUTO_INCREMENT, FOREIGN KEY, UNIQUE, NOT NULL.**

```sql
CREATE TABLE users (
    id    INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(100) UNIQUE NOT NULL,
    name  VARCHAR(100) NOT NULL
);

CREATE TABLE orders (
    id      INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

Det kan jeg!

**Can create DML (UPDATE, DELETE) statements.**

```sql
UPDATE users SET name = 'Bob' WHERE id = 1;
DELETE FROM users WHERE id = 1;
```

Jeg husker altid WHERE, ellers rammer det hele tabellen.

Det kan jeg!

**Can create a pull request.**

```bash
git checkout -b feature-branch
git add .
git commit -m "Add feature"
git push origin feature-branch
```

Bagefter går jeg ind på GitHub, klikker "Compare & pull request", skriver en beskrivelse og submitter.

Det kan jeg!

---

## Uge 6 - Advanced Git, Branching, YAML, GitHub Actions

**Understands different Git workflows such as GitHub Flow.**

- Jeg laver en branch ud fra main.
- Jeg laver mine ændringer på den branch.
- Jeg committer og pusher.
- Jeg åbner en pull request.
- Der bliver reviewet, og så merges den ind i main.

Kerneidéen:

- main skal altid kunne deployes.
- Selve arbejdet sker i feature-branches.

**Can solve a merge conflict.**

- Den opstår når to branches har ændret de samme linjer. Git markerer det med
  `<<<<<<<`, `=======` og `>>>>>>>`.
- Jeg åbner filen, vælger hvad der skal beholdes (eller kombinerer det) og fjerner markørerne.
- Så markerer jeg den som løst:

```bash
git add .
git commit -m "Resolve merge conflict"
```

Det kan jeg!

**Can write YAML.**

```yaml
name: My Workflow
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Say hello
        run: echo "Hello world"
```

Reglerne jeg holder mig til:

- Indrykning med mellemrum, aldrig tabs.
- Key-value format: `key: value`.
- Lister skrives med `-`.

Det kan jeg!

**Understands what GitHub Actions are and can breakdown workflows into runners, jobs, and steps.**

GitHub Actions er et værktøj til at automatisere opgaver (build, test, deploy) inde i GitHub.

Sådan deler jeg det op:

- Workflow - hele YAML-filen i `.github/workflows/`.
- Runner - maskinen jobbet kører på (fx ubuntu-latest).
- Job - en gruppe af steps.
- Step - en enkelt kommando eller opgave (`run`), eller en færdig action (`uses`).

```yaml
jobs:
  build:
    runs-on: ubuntu-latest   # runner
    steps:
      - run: echo "Step 1"
      - run: echo "Step 2"
```

**Can give use cases for GitHub Actions.**

- CI (Continuous Integration): kør tests automatisk ved hvert push.
- CD (Continuous Deployment): deploy app'en til en server eller cloud (Azure).
- Andet: tjekke kodeformat og linting, og sende notifikationer.

Det kan jeg give eksempler på!

---

## Uge 7 - Azure Web App Deployment

**Understands different cloud service models: IaaS, PaaS, SaaS.**

IaaS (Infrastructure as a Service):

- Jeg styrer: OS, runtime, apps.
- Udbyderen styrer: hardware og netværk.
- Eksempel: Azure Virtual Machines. Det er som at leje en computer i skyen.

PaaS (Platform as a Service):

- Jeg styrer: min applikation.
- Udbyderen styrer: OS, runtime og infrastruktur.
- Eksempel: Azure App Service. Jeg uploader bare koden, resten klares for mig.

SaaS (Software as a Service):

- Jeg bruger bare softwaren, og udbyderen styrer alt.
- Eksempel: Gmail. Det er som at bruge en app i browseren.

**Can deploy a web application to Azure App Service.**

- Jeg opretter en App Service i Azure.
- Jeg vælger runtime (Java) og region.
- Jeg kobler GitHub-repoet på og sætter deployment op via GitHub Actions.
- Jeg pusher kode, og så deployes app'en automatisk.

```yaml
- name: Build with Maven
  run: mvn clean package -DskipTests

- name: Deploy to Azure Web App
  uses: azure/webapps-deploy@v3
  with:
    app-name: 'giftr'
    publish-profile: ${{ secrets.AZURE_PUBLISH_PROFILE }}
    package: 'target/*.jar'
```

Det kan jeg! Giftr kører deployet på Azure App Service.

**Understands the flow from pushing, GitHub Actions running, building the project and deployment to Azure.**

1. Jeg pusher kode til main.
2. GitHub Actions trigges automatisk (på `on: push`).
3. En runner spinner op, checker koden ud og sætter Java og Maven op.
4. Build-step: Maven bygger projektet til en jar (`mvn clean package`).
5. Deploy-step: jar'en udrulles til Azure App Service med en publish profile fra GitHub Secrets.
6. Azure starter den nye version, og app'en er live.

Pointen er at mine hemmeligheder (publish profile, db-password) ligger i GitHub Secrets
og i Azure-config, ikke i selve koden.

---

## Uge 8 - Database i Spring + MySQL i Azure

**Adding a database to a Spring Project.**

- Jeg tilføjer MySQL-driveren og Spring JDBC i `pom.xml`.
- Jeg sætter forbindelsen op i `application.properties`.
- Jeg bruger `JdbcTemplate` i mine repositories.

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/giftr
spring.datasource.username=${DB_USER}
spring.datasource.password=${DB_PASSWORD}
```

```java
@Repository
public class UserRepository {
    private final JdbcTemplate jdbcTemplate;

    public UserRepository(JdbcTemplate jdbcTemplate) {
        this.jdbcTemplate = jdbcTemplate;
    }

    public List<User> findAll() {
        return jdbcTemplate.query("SELECT * FROM users",
            (rs, rowNum) -> new User(rs.getInt("id"), rs.getString("email")));
    }
}
```

Det kan jeg!

**Setting up a database in Azure.**

- Jeg opretter en Azure Database for MySQL (flexible server) i portalen.
- Jeg sætter admin-bruger og password.
- Jeg åbner firewall-regler, så min egen IP og App Service kan forbinde.
- Jeg opretter databasen og kører mine DDL-scripts mod den.

**Can set up a database in Azure and connect it to an Azure App Service project with a guide.**

- Jeg sætter forbindelsesoplysningerne som app settings / environment variables i Azure, ikke i koden.
- Spring læser dem via `${...}`:

```properties
spring.datasource.url=jdbc:mysql://giftr-db.mysql.database.azure.com:3306/giftr?useSSL=true
spring.datasource.username=${DB_USER}
spring.datasource.password=${DB_PASSWORD}
```

- `DB_USER` og `DB_PASSWORD` sætter jeg som app settings i App Service.
- Så er app'en i skyen koblet til databasen i skyen.

Det kan jeg med en guide, hvilket også er det målet kræver.

---

## Uge 9 - Database Transactions (Concurrency, ACID, Threads)

**Is able to go through scenarios that can cause concurrency problems in databases.**

De typiske problemer når flere ting sker samtidig:

- Dirty read: jeg læser data en anden har ændret, men ikke committet endnu.
- Non-repeatable read: jeg læser den samme række to gange og får forskellige værdier.
- Phantom read: den samme query giver nye rækker anden gang jeg kører den.
- Lost update: to skriver til den samme værdi, og den ene overskriver den andens ændring.
- Deadlock: to transaktioner venter på hinandens låse og kommer aldrig videre.

Eksempel: to brugere reserverer det sidste sæde på samme tid, og uden styring får de begge "ja".

**Can explain what ACID is and why it solves concurrency problems for databases.**

ACID er fire egenskaber en transaktion skal have:

- Atomicity: enten kører hele transaktionen, eller intet af den (rollback ved fejl).
- Consistency: databasen går fra én gyldig tilstand til en anden, og constraints overholdes.
- Isolation: samtidige transaktioner forstyrrer ikke hinanden.
- Durability: når noget først er committet, er det gemt permanent, også selvom strømmen går.

Grunden til at det løser problemerne: Atomicity og rollback fjerner halve updates og lost updates,
og Isolation forhindrer dirty, non-repeatable og phantom reads. SQL-databaser som MySQL er
ACID-compliant. Nogle NoSQL bruger i stedet BASE med "eventual consistency".

Det kan jeg forklare!

**Is aware of the possibility to define transactions in SQL and JDBC.**

I rå JDBC slår jeg auto-commit fra, kører mine queries og committer (eller ruller tilbage ved fejl):

```java
connection.setAutoCommit(false);
try {
    statement.executeUpdate("UPDATE seats SET status = 'reserved' WHERE seat_id = 1");
    connection.commit();    // alt lykkedes
} catch (SQLException e) {
    connection.rollback();  // noget fejlede, så fortryd
}
```

I Spring bruger jeg `@Transactional`, så styrer Spring selv commit og rollback:

```java
@Transactional
public void reserveSeat(int seatId) {
    // kaster metoden en exception, ruller Spring automatisk tilbage
}
```

Jeg er bevidst om det. Målet er "is aware", ikke at bygge det fra bunden.

**...and atomic structures (tråde / atomare operationer).**

- En atomar operation sker enten helt eller slet ikke, den kan ikke afbrydes halvvejs.
- Det er vigtigt når flere tråde rører den samme data samtidig, ellers får jeg en race condition.
- Det er den samme grundtanke som atomicity i databaser, bare på kode-niveau. I kode løser jeg det
  med låse eller atomare typer, og i databasen løser jeg det med transaktioner.

---

## Egenvurdering

- De fleste "can"-mål sidder fint, fordi jeg har brugt dem i Mandatory I (SQL) og i
  Giftr (Spring, Azure, GitHub Actions).
- Det jeg vil læse lidt ekstra op på er hurtig talsystem-omregning i hånden, Azure MySQL
  flexible server uden guide, og at forklare hele deploy-flowet roligt i den rigtige rækkefølge.
- Resten føler jeg mig klar til at vise mundtligt og med kode.
