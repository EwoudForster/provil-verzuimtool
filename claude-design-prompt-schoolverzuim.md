# Claude Design Prompt: Registratietool Schoolverzuim PROVIL

Kopieer onderstaande prompt in Claude Design (claude.ai) om een interactief prototype te genereren.

---

## Prompt

Maak een complete, interactieve webapp (React) voor het registreren en opvolgen van problematisch schoolverzuim op een school genaamd "PROVIL". De app wordt gebruikt door zorgcoordinatoren, CLB-medewerkers en leerkrachten. Gebruik een modern, clean design met een professionele maar warme uitstraling. Gebruik localStorage voor data-persistentie.

### Navigatie & Layout

- **Sidebar links** met:
  - Logo/titel "PROVIL Verzuimtool 2025-2026"
  - Navigatie-items: Dashboard, Leerlingen, CLB Overzicht, Instellingen
  - Onderaan: donker/licht-modus toggle
- **Hoofdgebied rechts** met breadcrumb en content

### 1. Dashboard (startpagina)

- **Statistiekkaarten bovenaan:**
  - Totaal aantal leerlingen in opvolging
  - Aantal per niveau (Niveau 1 = groen, Niveau 2 = oranje, Niveau 3 = rood)
  - Aantal actieve CLB-trajecten
  - Aantal nieuwe registraties deze maand
- **Grafiek:** horizontale staafgrafiek die per onderwijsvorm het aantal leerlingen per niveau toont
- **Recente activiteit:** lijst van laatste 5 toegevoegde/gewijzigde fiches

### 2. Leerlingen-overzicht

- **Filterbalk bovenaan:**
  - Zoekbalk (zoek op naam of klas)
  - Dropdown: Onderwijsvorm (Alle / DBSO / OKAN / 1e graad / 2e graad A / 2e graad D / 2e graad DA / 3e graad A / 3e graad D / 3e graad DA)
  - Dropdown: Inschaling (Alle / Niveau 1 / Niveau 2 / Niveau 3)
  - Dropdown: CLB-status (Alle / Consult / Traject)
  - Dropdown: Fase (Alle / In opstart / Lopende / Moeizaam / Afgerond)
- **"+ Nieuwe leerling" knop** (blauw, prominent)
- **Tabel** met kolommen:
  - Naam leerling (klikbaar, opent dossier)
  - Klas
  - Onderwijsvorm (badge/tag)
  - B-codes (getal, rood als hoog)
  - D-codes (getal)
  - Inschaling (kleur-badge: groen/oranje/rood)
  - CLB-status
  - Fase CLB-traject
  - Evolutie (pijl omhoog groen / pijl omlaag rood / horizontaal grijs)
  - Laatste update (datum)
- Sorteerbaar op elke kolom
- Paginering onderaan

### 3. Leerlingfiche (detail/bewerken)

Wanneer je op een leerling klikt, opent een **volledig dossier** als nieuwe pagina:

**Header:**
- Naam leerling (groot)
- Klas + onderwijsvorm als badges
- Inschaling-badge met kleur (automatisch berekend)
- "Bewerken" knop

**Tabbladen in het dossier:**

#### Tab: Overzicht
- **Twee kolommen:**
  - Links: Basisgegevens (naam, klas, onderwijsvorm, datum registratie)
  - Rechts: B-codes en D-codes met +/- knoppen om aan te passen, inschaling wordt automatisch herberekend
- **Automatische inschaling-logica:**
  - De drempelwaarden worden opgehaald uit Instellingen
  - Standaard: Niveau 1 = 1-5 B / 0-10 D, Niveau 2 = 6-10 B / 10-20 D, Niveau 3 = 10+ B / 20+ D
  - Toon een uitlegbalkje waarom dit niveau is toegekend

#### Tab: Acties & Afspraken
- **Sectie "Schoolacties"** - checkboxlijst:
  - Brief 5 B-codes verstuurd
  - Huisbezoek
  - Klastitularis betrekken
  - Melding schoolverzuim bij de politie
  - Ouders uitgenodigd op school
  - Persoonlijk gesprek met de leerling
  - Telefonisch contact
- **Sectie "Gemaakte afspraken op consult"** - tekstveld
- **Sectie "Doel gemaakte afspraken"** - tekstveld

#### Tab: CLB-opvolging
- **CLB consult of traject:** radio-buttons (Consult / Traject)
- **Naam consulter/trajecter:** tekstveld
- **CLB-traject acties** - checkboxlijst:
  - Gesprek met de leerling
  - Gesprek met ouders en leerling
  - Huisbezoek
  - Telefonisch contact met de ouders
- **Doel CLB-traject:** tekstveld
- **Fase CLB-traject:** dropdown (In opstart / Lopende / Moeizaam / Afgerond)
- **Evolutie t.a.v. vorig overleg:** radio-buttons (Positief / Negatief / Status quo)

#### Tab: Externe diensten
- **Checkboxlijst betrokken diensten:**
  - GGZ (Mentale problemen)
  - JAC (Jongerenhulp)
  - OCMW (Sociale/financiele hulp)
  - NAFT (Gedrags- of motivatieproblemen)
  - Buurtwerk (Gezin/buurtcontext)
  - Politie (Ernstig schoolverzuim)
  - CDE (Leerplichtopvolging)
- Per aangevinkte dienst: optioneel notitieveld

#### Tab: Tijdlijn
- Chronologisch overzicht van alle wijzigingen aan het dossier
- Elke entry toont: datum, type wijziging, details
- Meest recente bovenaan

#### Tab: Opmerkingen
- Lijst van notities met datum
- "Nieuwe opmerking toevoegen" tekstveld + knop
- Opmerkingen zijn niet bewerkbaar na opslaan (alleen verwijderbaar)

### 4. CLB Overzicht

Een speciale view voor CLB-medewerkers:
- **Gefilterd op** leerlingen met actief CLB-traject
- **Gesorteerd op:** eerst niveau (hoogste eerst), dan onderwijsvorm
- **Kolommen:** Naam, Klas, Onderwijsvorm, B-codes, D-codes, Niveau, Fase, Evolutie, Consulter
- **Kleurcodering per rij:** licht rood voor niveau 3, licht oranje voor niveau 2
- **Snelle actie-knoppen:** status wijzigen, notitie toevoegen

### 5. Instellingen

- **Drempelwaarden per onderwijsvorm:**
  - Tabel met per onderwijsvorm de B-code en D-code grenzen voor niveau 1, 2, 3
  - Bewerkbaar met inline editing
- **Schooljaar:** tekstveld (standaard "2025-2026")
- **Export:** knop om alle data te exporteren als CSV of JSON
- **Import:** mogelijkheid om een JSON-bestand te importeren

### Stijl & UX richtlijnen

- **Kleuren:** Gebruik een rustig kleurenpalet. Primair: blauw (#2563EB). Niveau 1: groen (#22C55E), Niveau 2: oranje/amber (#F59E0B), Niveau 3: rood (#EF4444)
- **Font:** Inter of system font stack
- **Spacing:** Ruim, veel witruimte, niet overladen
- **Responsive:** Werkt op desktop en tablet
- **Taal:** Alles in het Nederlands
- **Lege staat:** Toon een friendly illustratie/tekst wanneer er nog geen leerlingen zijn ("Nog geen leerlingen toegevoegd. Klik op + om te beginnen.")
- **Bevestigingen:** Toon een bevestigingsdialoog bij verwijderen
- **Toasts/notificaties:** Korte bevestiging bij opslaan ("Leerling opgeslagen")

### Voorbeelddata

Voeg 5 voorbeeldleerlingen toe zodat het prototype meteen gevuld is:
1. Jos - Klas 1A - 1e graad - 1 B-code, 5 D-codes - Niveau 3 - CLB traject lopende
2. Fatima - Klas 3B - OKAN - 8 B-codes, 3 D-codes - Niveau 2 - CLB consult
3. Mohammed - Klas 5A - 3e graad D - 12 B-codes, 22 D-codes - Niveau 3 - CLB traject moeizaam
4. An - Klas 2C - 2e graad A - 3 B-codes, 2 D-codes - Niveau 1 - Geen CLB
5. Bram - Klas 4D - DBSO - 6 B-codes, 15 D-codes - Niveau 2 - CLB traject in opstart
