# Project Overview — 99names

## Wat dit project is
Dit project is een **kennis- en verwerkingsinfrastructuur** rond islamitische brondata, met nadruk op:

- vertaling
- analyse
- documentatie
- herleidbaarheid
- structurele zorgvuldigheid

Het project is expliciet **geen applicatie**, geen website en geen product met een roadmap.
Het is een **werkende kennisfabriek**.

---

## Wat dit project niet is
Dit project is niet:

- een hobby-repo
- een experimenteel ML-lab
- een snelle proof-of-concept
- een platform voor “even iets proberen”
- een plek voor impliciete beslissingen

Snelheid en elegantie zijn ondergeschikt aan **begrijpelijkheid en overdraagbaarheid**.

---

## Kernprincipes

### 1. Eén waarheid
Er is één projectcontext en één set leidende documenten.

- Beslissingen staan in `DECISIONS.md`
- Rollen staan in `/roles/`
- Processen staan in `WORKFLOW.md`

Afwijkingen zonder vastlegging bestaan niet.

---

### 2. Scheiding van verantwoordelijkheden
Uitvoering, orkestratie, opslag, beoordeling en besluitvorming zijn **bewust gescheiden**.

Geen enkele rol:
- doet alles
- weet alles
- beslist alles

Dit is een ontwerpkeuze, geen organisatorisch toeval.

---

### 3. Alles wat telt wordt geschreven
Wat niet is vastgelegd:
- is niet gebeurd
- kan niet worden beoordeeld
- kan niet worden herhaald

Rapporten, reviews en beslissingen zijn geen bureaucratie maar **geheugen**.

---

### 4. Kritiek is extern
Echte kritiek komt van buiten het project.

Daarom zijn er expliciete externe review-modi:
- code review
- security review
- pentest
- red-team analyse

Deze rollen implementeren niets en beslissen niets.

---

## Structuur (hoog niveau)

├── PROJECT_OVERVIEW.md ← dit document
├── DECISIONS.md ← bindende keuzes
├── WORKFLOW.md ← hoe werk beweegt
├── ROLES.md ← rolindex
├── roles/ ← interne rollen
├── reports/ ← inhoudelijke output
├── reviews/ ← externe beoordelingskaders
└── Prompts/ ← rolgebonden prompts


Deze structuur is intentioneel.
Wijzigingen vereisen een beslissing.

---

## Hoe dit project te benaderen

Als je:
- iets wilt **uitvoeren** → kijk naar je rol
- iets wilt **beoordelen** → kijk naar `/reviews/`
- iets wilt **veranderen** → kijk naar `DECISIONS.md`
- iets wilt **begrijpen** → begin hier en lees verder

Begin niet met code.
Begin niet met tooling.
Begin met context.

---

## Besluitvorming
Er is één rol die besluiten neemt:
- **Project Owner / Architect**

Alle andere rollen:
- voeren uit
- beoordelen
- signaleren
- documenteren

Niet beslissen.

---

## Slot
Dit project is zo opgezet dat het:
- langzaam kan groeien
- kritiek kan verdragen
- overdraagbaar blijft
- niet afhankelijk is van individueel geheugen

Als dit alles overdreven aanvoelt, is dit project waarschijnlijk niet wat je zoekt.

Dat is geen probleem.
Dat is een filter.
