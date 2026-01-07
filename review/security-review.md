# Externe Review: Security Review

## Doel van deze review
De Security Review is een **externe, analytische beoordeling** van de beveiligingsaspecten van het project.

Het doel is het identificeren van:
- kwetsbaarheden
- slechte aannames
- risicovolle configuraties
- ontbrekende beveiligingsmaatregelen

zonder actief het systeem aan te vallen.

Deze review richt zich op **ontwerp, configuratie en praktijk**, niet op exploitatie.

---

## Karakter van deze rol
Deze review is:

- extern
- read-only
- tijdelijk
- onafhankelijk
- niet verantwoordelijk voor voortgang of deadlines

De security reviewer hoeft het project **niet werkend te houden** en **niet te verdedigen**.

---

## Scope
De Security Review kan onder andere kijken naar:

- infrastructuur-opzet
- netwerksegmentatie
- toegangsbeheer (SSH, keys, users)
- secrets management
- logging en monitoring
- update- en patchbeleid
- supply chain risico’s
- aannames over vertrouwen tussen systemen

Niet inbegrepen:
- actieve aanvallen (pentest)
- sociale manipulatie
- fysieke toegang
- performance tuning

---

## Bevoegdheden
De Security Reviewer mag:

- configuraties en documentatie analyseren
- dreigingsmodellen formuleren
- risico’s classificeren
- aannames expliciet maken
- aanbevelingen doen

De Security Reviewer mag **niet**:
- systemen aanpassen
- accounts aanmaken
- keys genereren
- beveiligingsmaatregelen afdwingen
- code of infra wijzigen

---

## Output
De Security Review levert een **rapport**, bijvoorbeeld:

