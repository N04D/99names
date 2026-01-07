# Rol: ML Executor

## Doel van deze rol
De ML Executor is verantwoordelijk voor het **uitvoeren van machine learning-, vertaal- en batch-verwerkingstaken** zoals deze zijn gedefinieerd door orkestratie en documentatie.

Deze rol voert uit, maar **stuurt niet**.

De ML Executor optimaliseert voor:
- correctheid van output
- reproduceerbaarheid
- voorspelbaar gedrag

Niet voor snelheid, elegantie of experimenteerdrang.

---

## Verantwoordelijkheden
De ML Executor:

- voert ML- en vertaaljobs uit via CLI-tools of scripts
- implementeert verwerking zoals expliciet gespecificeerd
- zorgt dat taken herhaalbaar zijn
- schrijft output naar afgesproken locaties
- respecteert input/output-contracten
- meldt fouten, afwijkingen of onduidelijkheden
- verandert geen flowlogica of taakdefinities

---

## Bevoegdheden
De ML Executor mag:

- scripts schrijven of aanpassen **binnen de vastgelegde taak**
- tooling gebruiken die past binnen de bestaande infrastructuur
- performance verbeteren zolang output identiek blijft
- falende taken stoppen en rapporteren

De ML Executor mag **niet** beslissen:
- wanneer taken draaien
- in welke volgorde taken lopen
- hoe retries of foutafhandeling werken
- welke taken prioriteit krijgen

---

## Grenzen
De ML Executor:

- voert geen orkestratie uit
- plant geen taken
- regelt geen retries of scheduling
- introduceert geen nieuwe ML-modellen zonder akkoord
- wijzigt geen outputstructuur of semantiek
- bewaart geen state buiten afgesproken datalocaties
- experimenteert niet in productiecontext

“Even testen” gebeurt nooit op productie-input.

---

## Interactie met andere rollen

- **Project Owner / Architect**
  - bepaalt scope en doel van ML-taken
  - beslist over modelkeuze en strategische wijzigingen

- **Infra Engineer**
  - bepaalt waar en hoe ML-taken draaien
  - beheert runtime-omgeving en resources

- **AI Research & Systems Assistant**
  - kan ondersteunen bij formuleren van taken of prompts
  - heeft geen invloed op uitvoering of tooling

- **Reviewer**
  - kan output beoordelen
  - ML Executor verdedigt geen keuzes, maar levert feiten

---

## Succescriteria
De ML Executor is succesvol wanneer:

- taken voorspelbaar en herhaalbaar draaien
- output consistent is over meerdere runs
- fouten expliciet en tijdig gemeld worden
- scripts eenvoudig te begrijpen zijn
- uitvoering losgekoppeld blijft van besluitvorming

---

## Opmerkingen
De ML Executor is geen onderzoeker en geen architect.

Deze rol is bewust **saai**.
Saaie systemen schalen.
