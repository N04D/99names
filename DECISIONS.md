Natuurlijk. Nog een document om toekomstige chaos preventief te beledigen 😌
Dit is een **DECISIONS.md** template dat je letterlijk kunt gebruiken.
Kort genoeg om niet genegeerd te worden, strak genoeg om vaagheid te blokkeren.

Zet dit in de root van je repo als `DECISIONS.md`.

---

# Architecture & Infrastructure Decisions

Dit document bevat **expliciete beslissingen** die de infrastructuur en architectuur vormgeven.

Doel:

* vastleggen *waarom* iets zo is opgezet
* voorkomen dat impliciete aannames verdwijnen
* zorgen dat keuzes reproduceerbaar en overdraagbaar zijn

Elke beslissing is bindend totdat deze **expliciet wordt herzien**.

---

## Decision Log

---

### Decision ID

`DEC-YYYY-MM-DD-XX`

### Titel

*Korte, beschrijvende titel van de beslissing*

---

### Context

Beschrijf kort:

* welk probleem of vraagstuk speelde
* welke beperkingen of randvoorwaarden er waren
* waarom deze beslissing nodig was

Geen geschiedenisles. Feiten volstaan.

---

### Beslissing

Beschrijf **exact** wat is besloten.

* Wat wordt gedaan?
* Waar wordt het geïmplementeerd?
* Wat wordt expliciet **niet** gedaan?

Gebruik concrete termen, geen intenties.

---

### Redenatie

Waarom is deze keuze gemaakt?

* technische overwegingen
* onderhoudbaarheid
* stabiliteit
* schaalbaarheid
* kennisoverdracht

Geen emotionele argumenten.

---

### Alternatieven overwogen

Noem minimaal 1 alternatief en **waarom het is afgewezen**.

Voorbeeld:

* CLI-only zonder orkestratie → afgewezen wegens onzichtbare state en beperkte traceerbaarheid

---

### Gevolgen

Wat betekent deze beslissing concreet?

**Positief**

* …

**Negatief / trade-offs**

* …

Geen perfecte keuzes. Benoem beide.

---

### Impact

* [ ] lokaal
* [ ] meerdere services
* [ ] hele infrastructuur

---

### Herziening

* Wordt deze beslissing ooit herzien?

  * [ ] nee
  * [ ] ja, bij: *(concrete trigger, geen “misschien later”)*

---

### Status

* [ ] voorgesteld
* [ ] aangenomen
* [ ] vervangen
* [ ] vervallen

---

### Datum

`YYYY-MM-DD`

### Betrokkenen

* naam / rol
* naam / rol

---

## Richtlijnen voor gebruik

* Elke **structurele** wijziging krijgt een decision
* Geen decision = geen wijziging
* Kleine implementatiedetails horen **niet** hier
* Dit document beschrijft **waarom**, niet **hoe**

---

## Slotregel

> *Als een keuze niet belangrijk genoeg is om vast te leggen,
> is hij niet belangrijk genoeg om de infrastructuur te veranderen.*

---

Als volgende stap kan ik:

* 2–3 **eerste concrete beslissingen** voor jouw huidige setup invullen
* of een **lichte variant** maken voor snelle beslissingen
* of dit koppelen aan Git PR-richtlijnen

Zeg maar wat je wilt verankeren.


Goed. Dan zetten we meteen **een echte, dragende beslissing** neer.
Niet cosmetisch. Niet vrijblijvend. Dit is de **fundering waar alles aan hangt**.

Je kunt dit **1-op-1** onderaan `DECISIONS.md` plakken.

---

## Decision Log

---

### Decision ID

`DEC-2026-01-06-01`

### Titel

Scheiding van orkestratie, uitvoering en state over afzonderlijke devices

---

### Context

Het project vereist betrouwbare batch-verwerking van tekst- en onderzoeksdata met de mogelijkheid tot toekomstige uitbreiding (zoals lokale LLM-inferentie), zonder herbouw van de basisinfrastructuur.

Er is gekozen voor een multi-device setup (Raspberry Pi’s en Odroid UX4). De centrale vraag was of taken gecombineerd moesten worden op één machine (CLI-only aanpak) of gescheiden over meerdere machines met duidelijke rollen.

Belangrijke randvoorwaarden:

* geen lokale GPU/PC op dit moment
* focus op stabiliteit en onderhoudbaarheid
* meerdere betrokkenen met verschillende expertise
* noodzaak tot auditbaarheid en overdraagbaarheid

---

### Beslissing

De infrastructuur wordt opgezet met **strikte scheiding van verantwoordelijkheden per device**:

* **Orkestratie** (planning, retries, flowlogica) draait uitsluitend op `rpi5-n8n`
* **Uitvoering / compute** (ML, vertaling, preprocessing) draait uitsluitend op `rpi5-ml`
* **State en data** (datasets, output, logs, databases) leven uitsluitend op de Odroid UX4
* **Code, scripts en documentatie** worden beheerd via self-hosted Git op `rpi3`

Geen enkel device combineert orkestratie, zware uitvoering en langdurige state.

---

### Redenatie

Deze scheiding is gekozen om:

* impliciete state in scripts te vermijden
* falen te isoleren tot één rol
* onderhoud en debugging eenvoudiger te maken
* toekomstige uitbreiding (bijv. lokale LLM op andere hardware) mogelijk te maken zonder herontwerp
* afhankelijkheid van individuele kennis te verminderen

Orkestratie vereist overzicht en controle, uitvoering vereist rekenkracht, en state vereist stabiliteit. Deze eisen conflicteren wanneer ze op één machine worden gecombineerd.

---

### Alternatieven overwogen

* **CLI-only aanpak zonder orkestratie**
  Afgewezen wegens:

  * verborgen flowlogica
  * gebrek aan zichtbaarheid en logging
  * moeilijk herstartbaar bij falen
  * beperkte schaalbaarheid

* **Alles op één device**
  Afgewezen wegens:

  * single point of failure
  * vermenging van verantwoordelijkheden
  * hogere kans op onvoorspelbaar gedrag

---

### Gevolgen

**Positief**

* heldere mentale en technische scheiding
* eenvoudiger onderhoud
* betere overdraagbaarheid
* toekomstige uitbreiding zonder herbouw

**Negatief / trade-offs**

* extra netwerkcommunicatie tussen devices
* iets meer initiële setup-complexiteit

Deze trade-offs worden acceptabel geacht.

---

### Impact

* [ ] lokaal
* [ ] meerdere services
* [x] hele infrastructuur

---

### Herziening

* Wordt deze beslissing ooit herzien?

  * [x] nee
  * [ ] ja, bij: n.v.t.

---

### Status

* [ ] voorgesteld
* [x] aangenomen
* [ ] vervangen
* [ ] vervallen

---

### Datum

`2026-01-06`

### Betrokkenen

* Project owner / architect
* Infra engineer

---

Dit is nu een **ankerbeslissing**.
Alles wat hierna komt:

* moet hiermee compatibel zijn
* of expliciet een *nieuwe* decision krijgen

Als je wilt, kan ik nu:

* Decision 02 invullen (bijv. *“n8n als orkestratielaag”*)
* of een **lichte review-check** maken: “raakt deze wijziging Decision 01?”

Maar deze staat. En die staat goed.
