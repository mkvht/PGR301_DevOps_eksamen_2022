# Eksamen 2022
## DevOps i Skyen

Dette er en arbeid gjort i forbindelse med kurs kode på Kristiania.
Oppnådd karakter: A

[![CI pipeline](https://github.com/mkvht/PGR301_eksamen_2022/actions/workflows/ci.yml/badge.svg)](https://github.com/mkvht/PGR301_eksamen_2022/actions/workflows/ci.yml)
[![Docker build](https://github.com/mkvht/PGR301_eksamen_2022/actions/workflows/docker.yml/badge.svg)](https://github.com/mkvht/PGR301_eksamen_2022/actions/workflows/docker.yml)
[![Terraform CloudWatch](https://github.com/mkvht/PGR301_eksamen_2022/actions/workflows/cloudwatch_dashboard.yml/badge.svg)](https://github.com/mkvht/PGR301_eksamen_2022/actions/workflows/cloudwatch_dashboard.yml)

### **Del 1:** DevOps-prinsipper
***[1.1] Hva er utfordringene med dagens systemutviklingsprosess - og hvordan vil innføring av DevOps kunne være med på å løse disse? Hvilke DevOps prinsipper blir brutt?***

Prinsippene til DevOps modellen er:
* Collaboration
* Automation
* Continuous Improvement and Delivery
* Customer-Centric Action
* Create with a goal in mind

En stor årsak til at DevOps utvikling har nylig blitt mer ettertraktet er DevOps sin egenskap til å organisere og effektivisere utviklingsprosessen. Tradisjonelt har utviklerteam, bygget opp av utviklerene (Dev, de som skaper produktet), og Operations (Ops, de som sørger for testing og deployment av produktet) jobbet i separate team. Dette har historisk ledet til dårlig eller manglende kommunikasjon mellom de to teamene. Ved å separere disse teamene oppstår det en "wall of confusion" hvor tekniske- og forståelsesproblemer dukker opp. Dette medfører at begge teamene potensiellt produserer waste (unødvendig arbeid) og at oppgaver kan ta mye lengre tid før alt er klart til deployment. I tillegg betyr det at om noe går galt etter deployment tar det mer tid og resusser til å rette opp i feilen. 

Det overnevnte er et stort problem i dag ettersom markedet har blitt ekstremt krevende. Kunder forventer oftest at programmene de bruker skal ha god ytelse, god oppfølging og oppdateres etter behov relativt raskt. Dette er noe som DevOps får til ved å gjøre om på hvordan teamene er satt sammen i tillegg til å gi tilgang til verktøy som gjør overgangen fra utvikling til operations mye enklere.

En stor del av DevOps er å identifisere "flaskehalser". Dette vil si, steder i utviklingsprosessen der arbeidet "stopper opp". Et eksempel kan være at en "Ops" ikke forstår hvorfor en "Dev" har gjordt spesifikke valg i koden. Om det oppstår spørsmål må de kontakte Dev teamet og vente på svar. Utfallet av dette kan være unødig tidsbruk, da Dev teamet ikke nødvendigvis er umiddelbart tilgengelig. Med DevOps kan man unngå disse problemene da utvikleren selv har ansvar for å vedlikeholde koden og utføre både "dev" og "ops" selv. På denne måten kan vi redusere flaskehalser.

Et vanskeligere DevOps prinsipp som ofte ikke følges opp korrekt er prinsippet om continuous deployment. DevOps prinsipper er ikke noen man kan implementere uten videre. En av de største årsakene til at DevOps kan faile er at man har forsøkt å implementere DevOps uten omtanke til hvordan det vil fungere sammen med eller påvirke andre relaterte prosjekter. I tillegg er det vanskelig å legge om et eksisterende prosjekt til DevOps. For eksempel må man tenke på om prosjektet bruker "Trunk-based development workflow" eller "Feature-based development workflow". I et Trunk-based development workflow prosjekt pusher man som regel all koden til kun en "branch" (main), mens i et Feature-based development workflow prosjekt pusher man inn i mange forskjellige branches i prosjektet hvor de senere blir merget inn i main. Med DevOps prinsippene burker man Feature-based workflow da det hindrer merge-conflicts om mange utviklere jobber på samme prosjekt. Dette tillater at man kan deploye små endringer ofte uten at man eksempelvis ødlegger for andre og at det i tillegg er eklere å gå tilbake om det skulle skje noe feil.

<br>
<br>

***[1.2] En vanlig respons på mange feil under release av ny funksjonalitet er å gjøre det mindre hyppig, og samtidig forsøke å legge på mer kontroll og QA. Hva er problemet med dette ut ifra et DevOps perspektiv, og hva kan være en bedre tilnærming?***

DevOps prinsippene peker mot mindre og hyppige deployments istedet for større. Dette er først og fremst fordi markedet er veldig krevende og kunder ønsker oftere å få rakse oppdateringer og fikser enn å vente lenger tid på store endringer. I tillegg er det ofte enklere og ryddigere for utviklerene når de skal pushe kode til prosjektet. Ved å pushe mindre biter med kode er det enklere for mange utviklere å jobbe sammen uten å skape merge-conflicts. Det er også enklere å finne "feil" i koden og hvor de kom inn. Om man pusher en liten ending istedet for en stor er det lettere for utvikleren å gå tilbake til den forrige versjonen som fungerte uten å miste masse kode og arbeid. Dette effektiviserer arbeidet og lager en mulighet for at en stor gruppe med utviklere kan ta annsvar for små oppgaver (en utvikler lager funksjon "addProduct" mens noen andre lager "listProduct") uten at de forstyrrer hverandres arbeid. 

<br>
<br>

***[1.3] Teamet overleverer kode til en annen avdelng som har ansvar for drift - hva er utfordringen med dette ut ifra et DevOps perspektiv, og hvilke gevinster kan man få ved at team han ansvar for både drift- og utvikling?***

Når et team jobber med både "dev" og "ops" kan man unngå "flaskehalser". Man reduserer muligheten for miskommunikasjon, "tapt kunnskap" (Utvikler kan ikke nødvendigvis bruke de samme verktøyene eller har samme kunnskap som drift-ansvarlig) og "the wall of confusion". I et tradisjonelt utviklermiljø der dev og ops jobber separat oppsår det oftere unødig tidsbruk på at dev og ops venter på svar fra hverandre eller at de ikke skjønner hvorfor det andre teamet mener noe er feil. Dette kan eksempelvis omhandle kodevalg eller tekniske feil relatert til verkøy (dev og ops bruker ikke nødvendigvis samme type verktøy).

<br>
<br>

***[1.4] Å release kode ofte kan også by på utfordringer. Beskriv hvilke- og hvordan vi kan bruke DevOps prinsipper til å redusere eller fjerne risiko ved hyppige leveraner.***

Om mange utviklere pusher kode til samme branch vil det øke sansynligheten for merge-conflicts som tar tid og nøyaktighet å løse. Derfor er det ofte brukt mindre hyppige leveranser der man jobber i mange forskjellige forker. Dette gjør også at utviklere kan gjøre feil og må gå tilbake til tidligere versjone. En måte DevOps prinsippene hindrer dette er å sette safeguards på main branchen slikt at ikke alle alltid kan merge feature-bancher mot main. Dette kan for eksempel være branch-protection, som kan gå gjennom en sjekk liste med requirements før man kan gjøre en merge. Dette minsker sansynligheten for at man merger noe inn i main som kanskje ikke fungerer, kvalifiserer eller ikke består tester. 

<br>
<br>

### **Del 2:** CI
**Oppgave 1:**
Workflow kjører ved pull og push til master (gjordt)

**Oppgave 2:**
 - Enhetstester failet (gjordt)
 - Fikset enhetstester (Godkjent i github actions) + pipelines består
 - Workflowen kompilerer javakoden og kjører enhetstester på hver eneste push, *uavhengig av branch* (gjordt)

Lagt til GitHub Actions badge i README.md
**Oppgave 3:**

For å konfigurere branch protection i GitHub gjør vi følgende:
1. Naviger til hovedsiden av repositoriet det gjelder
2. Gå til repository *settings*
3. I venstre side-meny, under *Code and automation* velger vi *branches* og trykker derretter på *"Add branch protection rule"* og kommer til siden *Branch protection rule*
4. I feltet *"Branch name pattern"* skriver man inn **navnet på den branchen** man ønsker å beskytte. (For eksempel "main" eller "master")
5. Derretter får man alternativer man kan velge for beskyttelsen.
    * for eksempel *Require a pull request before merging* og *Require status checks to pass before merging*

For å hindre direkte push til main/master (i dette prosjektet er det master) finnes det flere fremgangsmetoder:
* Under *Branch protection rule* siden finnes det et alternativ som heter *"lock branch"*. *Lock branch* gjør branchen til en read-only branch hvor man ikke for lov til å pushe noe inn i branchen.
    * Man kan lage spesifike regler for brukere der de kan ha tillatelse til å "bypass branch protection" slikt at for eksempel admin kan gjøre en merge.
* En annen måte er å velge alternativet *Require a pull request before merging* sammen med underalternativet *Require Approvals*. Dette gjør at alle commits fra en ikke-beskyttet branch mot den beskyttede branchen må gjennom en code review før de kan merges til den beskyttedet branchen. I tillegg kan man velge hvor mange godkjenninger som må til før pushet går igjennom)
    * Man kan også benytte seg av alternativet *Require review from Code Owners* som gjør at eieren av koden må godkjenne pushet før det går gjennom.

For å hindre merge til main/master fra feature branchen uten at den er verifisert av GitHub Actions kan vi ruke denne metoden.
* Under *Branch protection rule* siden velger vi alternativet *Require status checks to pass before merging*.
    * Denne reglen gjør at GitHub Actions build må bestå før fature branchen kan merge til main/master.

<br>

### **Del 3:** Docker
**Oppgave 1:**

Beskriv hva du må gjøre for å få workflow til å fungere med din DockerHub konto? Hvorfor feiler workflowen? 
<br>

For å få workflowen til å fungere må man legge til *GitHub secrets* som ```docker.yml``` filen leser ut. Secret infoen nødvendig er brukernavn og token fra dockerhub kontoen.
Årsaken til at workflowen failer uten brukernavnet og tokenet til DokerHub kontoen er fordi man må være verifisert og ha tillatelse til å koble seg til DockerHub. Dette gjelder selfølgelig ikke bare når jeg som bruker vil ha tilgang men også når andre porgrammer trenger tilgang.

**Oppgave 2:**
<br>
FROM adoptopenjdk/openjdk 8 endret
Opprydding i ```DockerFile``` utført
Opprydding i ```docker.yml```

**Oppgave 3:**
<br>
Eget ECR repo opprettet med navn 1004 <br>
```docker.yml``` pusher til Amazon ECR
<br>

For at sensor skal kunne pushe til sitt eget ECR fra egen fork:

1. Fra Console Home i AWC finn *IAM* (Identity and Access Management).
2. I venste side-meny gå til *users* og finn din bruker.
3. Gå til tabben *security credentials* og trykk på knappen *Create access key*. Lagre filen som blir generert her. Om du mister dette finner du det ikke igjen og må starte på nytt.
4. Inne i GitHub prosjektet går vi til *settings*
5. I venstre side-meny velger vi *secrets* og derretter *Actions*
6. Trykk på *New repository secret* (vi skal opprette 2).
    * Lag en secret med navnet: **AWS_ACCESS_KEY_ID**
        * Lim inn din **Access key ID** (Ligger i IAM-filen du lastet ned tidligere)
    * Lag en secret med navnet: **AWS_SECRET_ACCESS_KEY**
        * Lim inn din **Secret access key** (Ligger i IAM-filen du lastet ned tidligere)
7. Inne i ```.github/workflows ``` i repoet finner du filen: ```docker.yml```
    * Finn *REPO env* og endre til egen repo adresse.
        * REPO: 244530008913.dkr.ecr.eu-west-1.amazonaws.com/1004 (1004 må byttes ut med ditt repo navn)




### **Del 4:** Metrics, overvåkning og alarmer
Gjør nødvendige endringer i ```pom.xml``` - og koden, slik at applikasjonen kan levere Metrics til CloudWatch ved hjelp av Spring Boot Micrometer (gjordt)

Konfigurer applikasjonen til å bruke ditt eget ClodWatch Metrics Namespace - ditt Kandidatnummer. (gjordt)

Slettet hele test mappen(gjordt)

Endre Javakoden slik at den rapporterer følgende Metrics til CloudWatch:
* "carts" (done)
* "cartsvalue" (done)
* "checkouts" (done)
* "checkout_latency" (done)

### **Del 5:** Terraform og CloudWatch Dashboards

**Oppgave 1**
Terraform forsøker å lage en s3 bucket uten at det eksisterer en terraform.state fil. Derfor vil ikke terraform skjønne at bucketen allerede eksisterer.
Lagde en terraform.state fil og kjørte
```
$ terraform import aws_s3_bucket.analytics-bucket analytics-1004

$ terraform apply
```

**Oppgave 2**
Workflow filen ```cloudwatch_dashboard.yml``` filen endret slik at apply bare bli kjørt på push mot main branch, og terraform plan på når det lages en Pull request (done)

**Oppgave 3**
* CloudWatch Dashboard med *fire widgets* (done)
* Antall handlekurver på et gitt tidspunkt i tid (done)
* Total sum med penger i handlekurver på et gitt tidspunkt i tid (done)
* Gjennomsnittlig responstid for Checkout metoden i Controller-klassen. (done)

### Alarmer
(fullført)
