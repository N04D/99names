# Project Workflow

Dit document beschrijft de **formele workflow** van dit project:  
hoe werk ontstaat, wordt beoordeeld, vastgelegd en eventueel leidt tot beslissingen.

Doel:
- voorkomen van impliciete besluiten
- scheiden van uitvoering, beoordeling en richting
- waarborgen van traceerbaarheid en overdraagbaarheid

Deze workflow is leidend.

---

## Overzicht (hoog niveau)

Uitvoering
↓
Rapport
↓
Review
↓
Beslissing (optioneel)
↓
Implementatie (optioneel)


Niet elke stap leidt automatisch tot de volgende.  
**Overslaan mag niet. Teruggaan wel.**

---

## Stap 1: Uitvoering

### Betrokken rollen
- ML Executor
- Infra Engineer
- (eventueel) AI Research & Systems Assistant

### Beschrijving
Een taak wordt uitgevoerd binnen vastgestelde kaders:
- bestaande beslissingen
- vastgelegde rolafbakening
- afgesproken infrastructuur

Uitvoering:
- verandert geen architectuur
- introduceert geen nieuwe uitgangspunten
- creëert geen impliciete besluiten

---

## Stap 2: Rapportage

### Verplicht document
- `/reports/<NAAM>_<YYYY-MM-DD>.md`
- volgens `REPORT_TEMPLATE.md`

### Doel
- vastleggen wat **feitelijk** is gebeurd
- scheiden van resultaat en interpretatie
- voorkomen dat kennis verdwijnt in hoofden of logs

Zonder rapport:
- bestaat het werk niet binnen het project

---

## Stap 3: Review

### Mogelijke review-vormen
- Interne review (`/roles/reviewer.md`)
- Externe reviews:
  - Code Review
  - Security Review
  - Pentest
  - Red-Team Analyse

### Verplicht document
- `/reviews/reports/<TYPE>_<YYYY-MM-DD>.md`
- volgens `REVIEW_TEMPLATE.md`

### Regels
- reviews zijn read-only
- reviewers implementeren niets
- reviewers nemen geen beslissingen
- kritiek is expliciet en onderbouwd

Een review kan:
- bevestigen
- problematiseren
- blokkeren
- vragen oproepen

Maar **niet oplossen**.

---

## Stap 4: Besluitvorming (optioneel)

### Betrokken rol
- Project Owner / Architect

### Wanneer nodig?
Een beslissing is vereist wanneer:
- structuur verandert
- scope wijzigt
- risico’s expliciet worden geaccepteerd
- rollen of verantwoordelijkheden verschuiven
- architectuurprincipes worden geraakt

### Vastlegging
- nieuwe entry in `DECISIONS.md`
- met datum, context en redenatie
- verwijzing naar rapport(en) en review(s)

Zonder vastgelegde beslissing:
- blijft de situatie ongewijzigd

---

## Stap 5: Implementatie (optioneel)

### Betrokken rollen
- Infra Engineer
- ML Executor

### Regels
- implementatie volgt expliciet uit een beslissing
- geen “interpretatie” van besluiten
- afwijkingen vereisen nieuwe review of beslissing

Implementatie zonder besluit is **ongeldig**.

---

## Escalatie en terugkoppeling

- Elke rol mag escaleren naar de Project Owner
- Onzekerheid is een geldige reden voor escalatie
- Stilzwijgende aannames zijn dat niet

Terugkoppeling verloopt altijd via documentatie, niet via mondeling overleg.

---

## Wat expliciet niet mag

- directe implementatie op basis van een review
- structurele wijzigingen zonder beslissing
- beslissingen zonder vastlegging
- “tijdelijke” oplossingen zonder documentatie
- shortcuts buiten deze workflow

---

## Slotregel

> Snelheid is tijdelijk.  
> Beslissingen zijn permanent.

Als het niet door deze workflow kan,
hoort het niet in dit project.
