---

# Infrastructure Overview

## Doel van deze infrastructuur

Deze infrastructuur is opgezet om **betrouwbare, herhaalbare batch-verwerking** mogelijk te maken voor tekst-, vertaal- en onderzoekswerk.

De nadruk ligt op:

* stabiliteit boven snelheid
* begrijpelijkheid boven slimheid
* scheiding van verantwoordelijkheden
* toekomstige uitbreiding zonder herbouw

Dit is **geen hobby-lab**, geen showcase en geen experimentele speeltuin.

---

## Architectuurprincipes

De infrastructuur volgt deze vaste principes:

* Eén machine = één primaire rol
* Orkestratie ≠ uitvoering
* State zit in data, niet in scripts
* Scripts zijn stateless en herhaalbaar
* Alles moet zonder context te begrijpen zijn

Deze principes zijn leidend. Afwijkingen worden expliciet vastgelegd.

---

## Overzicht van devices en rollen

### Raspberry Pi 5 – `rpi5-ml`

**Rol:** Uitvoering / compute

Deze machine voert batch-taken uit zoals:

* vertaaljobs via CLI
* preprocessing van data
* CPU-gebonden ML-taken

Eigenschappen:

* stateless
* geen planning
* geen beslissingen
* geen langdurige state

De machine **doet werk**, maar bepaalt nooit *wanneer* of *wat eerst*.

---

### Raspberry Pi 5 – `rpi5-n8n`

**Rol:** Orkestratie / regie

Deze machine draait:

* n8n
* schedulers
* workflowlogica
* retries en foutafhandeling

Eigenschappen:

* geen inhoudelijke verwerking
* geen ML
* geen zware compute

De machine **beslist**, maar voert zelf geen zwaar werk uit.

---

### Odroid UX4

**Rol:** Data- en servicelaag

Deze machine is verantwoordelijk voor:

* opslag van datasets
* output van batch-jobs
* logs
* databases (indien nodig)
* backups en integriteitscontrole

Eigenschappen:

* stabiel
* altijd aan
* waarheid zit hier

De UX4 bevat **state**. Andere machines niet.

---

### Raspberry Pi 3

**Rol:** Git & infra-hulpdiensten

Deze machine draait:

* self-hosted Git
* configuratie-repositories
* scripts
* prompts
* documentatie

Eigenschappen:

* licht
* betrouwbaar
* geen compute
* geen data-verwerking

Dit is het **geheugen van het project**.

---

## Data-structuur (Odroid UX4)

```text
/data
 ├── raw/            # ruwe input
 ├── processing/     # in behandeling
 ├── translated/     # vertaalde output
 ├── reports/        # samenvattingen / analyses
 ├── logs/           # run-logs
```

Deze structuur is leidend.
Scripts mogen hier niet van afwijken zonder expliciete reden.

---

## Orkestratie vs uitvoering

* **n8n** bepaalt:

  * wanneer een taak start
  * welke stap volgt
  * wat gebeurt bij falen

* **CLI-scripts**:

  * voeren exact één taak uit
  * kennen geen planning
  * kunnen veilig opnieuw draaien

Een script mag nooit:

* zelf retries regelen
* zelf plannen
* afhankelijk zijn van vorige runs

---

## Code & configuratie

* Alle scripts en configuraties staan in Git
* Configuratie en secrets zijn gescheiden van code
* Geen hardcoded paden of credentials
* Elke service heeft:

  * duidelijke naam
  * vaste loglocatie
  * eenvoudige start/stop-instructies

---

## Logging & foutafhandeling

* Elke batch-run schrijft logs
* Fouten zijn zichtbaar en herleidbaar
* Output wordt pas definitief bij succesvolle afronding
* Bij falen blijft input intact

Geen “stille fouten”.

---

## Wijzigingen en besluitvorming

Elke structurele wijziging aan de infrastructuur:

* wordt vastgelegd
* krijgt een duidelijke motivatie
* volgt de checklist in `Infra-Engineer`

Afwijkingen van deze README zijn toegestaan, maar **nooit impliciet**.

---

## Wat deze infrastructuur niet is

* Geen realtime systeem
* Geen interactieve omgeving
* Geen playground
* Geen plek voor slimme trucs

Alles wat hier draait moet:

* verklaarbaar zijn
* overdraagbaar zijn
* opnieuw op te zetten zijn

---

## Slot

Als iets niet eenvoudig uit te leggen is aan een nieuwe engineer,
dan hoort het hier niet thuis.

Stabiliteit wint altijd van elegantie.

---

Als je wilt, kan ik nu ook:

* een **DECISIONS.md** template maken
* een **onboarding README** voor nieuwe helpers
* of dit document **afstemmen op n8n / Docker / systemd** niveau

Maar voor nu:
dit is een solide ruggengraat.
