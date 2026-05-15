---
name: ai-governance
description: >-
  Helpt bij het beoordelen van AI-systemen op naleving van de EU AI Act
  (Verordening 2024/1689). Classificeert AI-systemen in risicocategorieën,
  checkt verplichte documentatie (technische documentatie, conformiteitsbeoordeling,
  risicomanagement), genereert EU AI Act compliance checklists, en adviseert
  over governance-structuren voor hoog-risico AI-systemen. Integreert met
  BIO2, IAMA en NORA voor Nederlandse overheidscontext.
  Gebruik deze skill wanneer de gebruiker vraagt over 'EU AI Act',
  'AI-verordening', 'AI governance', 'AI compliance', 'algoritme toezicht',
  'AI risicoclassificatie', 'hoog risico AI', 'conformiteitsbeoordeling AI',
  'AI transparantie', 'AI documentatieplicht', 'FRIA', 'fundamental rights',
  'AI toezichthouder', 'AI autoriteit', 'AI sandbox', 'IAMA', 'algoritmerisico',
  'discriminatie AI', 'bias AI', 'AI uitlegbaarheid', 'AI transparantie',
  'menselijk toezicht AI', 'human-in-the-loop AI', 'AI kwaliteitsmanagement',
  'AI incident melden', 'notified body AI', 'CE-markering AI',
  of wanneer de gebruiker een AI-systeem wil laten voldoen aan de EU AI Act.
model: sonnet
allowed-tools:
  - WebFetch(*)
  - Bash(gh api *)
  - Bash(gh search *)
---

# EU AI Act Compliance Checker

Toets AI-systemen aan de EU AI Act (Verordening 2024/1689). De AI Act is van kracht sinds 1 augustus 2024 met gefaseerde inwerkingtreding:

- **2 februari 2025**: Verbod op AI-praktijken met onaanvaardbaar risico (Art. 5)
- **2 augustus 2025**: Regels voor GPAI-modellen (Art. 53-55), sancties (Art. 99-100)
- **2 augustus 2026**: Volledige verplichtingen voor hoog-risico AI-systemen (Art. 6 + Annex III)
- **2 augustus 2027**: Verplichtingen voor hoog-risico AI uit productveiligheidslijst (Art. 6(1) + Annex I)

Bron: [EU AI Act full text](https://eur-lex.europa.eu/legal-content/NL/TXT/?uri=CELEX:32024R1689) | [AI Act Regulatory Timeline](https://artificialintelligenceact.eu/ai-act-timeline/)

## Risicoclassificatie

### Stap 1: Bepaal de risicocategorie

```
Is het AI-systeem verboden onder Art. 5?
  ├── Ja → ONAANVAARDBAAR RISICO (verboden)
  └── Nee
      └── Valt het onder Annex III (hoog-risico use cases)?
            ├── Ja → HOOG RISICO (Art. 6 + Annex III)
            └── Nee
                └── Is het een GPAI-model met systemisch risico?
                      ├── Ja → SYSTEMISCH RISICO (Art. 51-55)
                      └── Nee
                          └── Interageert het direct met natuurlijke personen?
                                ├── Ja → BEPERKT RISICO (transparantieplicht Art. 50)
                                └── Nee → MINIMAAL RISICO (vrijwillige codes of practice)
```

### Verboden AI-praktijken (Art. 5) — Onaanvaardbaar risico

| Praktijk | Kenmerken |
|----------|-----------|
| **Subliminale manipulatie** | Technieken onder het bewustzijn die gedrag wezenlijk verstoren |
| **Manipulatie van kwetsbaren** | Uitbuiting van kwetsbaarheden door leeftijd of handicap |
| **Social scoring** | Classificering van natuurlijke personen op basis van sociaal gedrag (zowel publiek als privaat) |
| **Individuele risicovoorspelling** | Profiling om crimineel gedrag te voorspellen op basis van persoonlijkheidskenmerken (uitzondering: objectieve feiten met menselijke beoordeling) |
| **Gezichtsdatabases scrapen** | Ongerichte scraping van internet/CCTV voor gezichtsherkenningsdatabases |
| **Emotieherkenning** | Op werkplek (uitzondering: medisch/veiligheid) en in onderwijs |
| **Biometrische categorisatie** | Op basis van gevoelige kenmerken (ras, politiek, religie, seksueel) — met uitzonderingen voor wetshandhaving |
| **Real-time biometrische identificatie** | In publieke ruimten voor wetshandhaving (beperkt: vermiste personen, terreurdreiging, ernstige misdrijven, met rechterlijke toestemming) |

### Hoog-risico AI-systemen (Art. 6 + Annex III)

**Annex III use cases — altijd hoog risico:**

| Domein | Use case |
|--------|----------|
| **Biometrie (excl. verboden)** | Biometrische identificatie op afstand (niet real-time), biometrische categorisatie (niet-gevoelig), emotieherkenning (buiten verbod) |
| **Kritieke infrastructuur** | Veiligheidscomponenten in beheer en aansturing van kritieke digitale infrastructuur, wegverkeer, water, gas, warmte, elektriciteit |
| **Onderwijs** | Toelating tot onderwijsinstellingen, toewijzing aan opleidingen, evaluatie van leerresultaten |
| **Werkgelegenheid** | Werving en selectie, prestatiebeoordeling, promotiebeslissingen, taaktoewijzing op basis van AI, beëindiging arbeidsrelatie |
| **Essentiële diensten** | Toegang tot publieke diensten, kredietwaardigheidsbeoordeling, risicobeoordeling levens-/ziektekostenverzekering |
| **Wetshandhaving** | Recidiverisicobeoordeling, leugendetectie, bewijsmateriaalanalyse, voorspelling van strafbare feiten (uitzondering: verboden profiling) |
| **Migratie** | Asiel- en visumbeoordeling, grenscontrole, risicobeoordeling irreguliere migratie |
| **Rechtspraak** | Rechtsfeitelijk onderzoek, interpretatie van rechtsregels, toepassing van recht |
| **Democratische processen** | Potentieel beïnvloeden van verkiezingsuitslagen of stemgedrag (uitzondering: informatievoorziening aan kiezers) |

**Art. 6(1) — productveiligheidslijn:** AI als veiligheidscomponent in producten onder EU-harmonisatiewetgeving (machines, medische hulpmiddelen, speelgoed, liften, radioapparatuur, etc.) die een derdepartij conformiteitsbeoordeling vereisen.

**Uitzondering op hoog-risico classificatie (Art. 6(3)):**
Een AI-systeem is GEEN hoog risico, ook al valt het onder Annex III, indien het:
- Een enge procedurele taak uitvoert
- Een eerdere menselijke activiteit verbetert of voltooit
- Beslissingspatronen detecteert zonder deze te vervangen
- Een voorbereidende taak uitvoert

MAAR: profiling maakt deze uitzondering ongeldig.

## Verplichtingen voor hoog-risico AI (Art. 8-29)

### 1. Risicomanagementsysteem (Art. 9)

Continue, iteratief proces gedurende de hele levenscyclus:

| Stap | Vereiste |
|------|----------|
| Risico-identificatie | Bekende en redelijkerwijs voorzienbare risico's in kaart brengen bij gebruik conform bestemming én redelijk voorzienbaar misbruik |
| Risico-analyse | Impact op gezondheid, veiligheid en grondrechten schatten; waarschijnlijkheid en ernst bepalen |
| Risico-evaluatie | Vergelijken met bestaande risico's zonder AI; bepalen of resterende risico's aanvaardbaar zijn |
| Risicobeperking | Passende maatregelen treffen voor elk geïdentificeerd risico; resterende risico's documenteren |
| Testprocedures | Testen voor gebruik in de markt brengen en na elke significante wijziging |

### 2. Datakwaliteit en datagovernance (Art. 10)

| Eisen voor training, validatie en test datasets |
|-------------------------------------------------|
| Relevante datagovernance- en beheerpraktijken |
| Onderzoek op bias die kan leiden tot discriminatie |
| Relevant, representatief, foutloos en compleet (zo veel mogelijk) |
| Rekening houden met geografische, contextuele en gedragskenmerken van de inzetomgeving |
| Verwerking van bijzondere persoonsgegevens voor bias-detectie onder strikte waarborgen |

### 3. Technische documentatie (Art. 11 + Annex IV)

Moet aantonen dat aan alle eisen is voldaan. Minimaal bevatten:

- Algemene beschrijving van het systeem (beoogd doel, versie, architectuur)
- Gedetailleerde beschrijving van de elementen en het ontwikkelproces
- Informatie over monitoring, functioneren en controle
- Beschrijving van het risicomanagementsysteem
- Beschrijving van wijzigingen gedurende levenscyclus
- Lijst van geharmoniseerde normen of andere technische specificaties
- EU-conformiteitsverklaring
- Resultaten van validatietests

### 4. Transparantie en gebruikersinformatie (Art. 13)

Hoog-risico AI-systemen moeten vergezeld gaan van een gebruiksinstructie met:

- Identiteit en contactgegevens van de aanbieder
- Kenmerken, mogelijkheden en beperkingen van het systeem
- Voorzienbare risico's voor gezondheid, veiligheid en grondrechten
- Niveau van nauwkeurigheid, robuustheid en cyberbeveiliging
- Menselijk toezicht-maatregelen
- Verwachte levensduur en onderhoudsmaatregelen

### 5. Menselijk toezicht (Art. 14)

Doel: risico's voorkomen of minimaliseren. De gebruiksinterface moet natuurlijke personen in staat stellen:

- Het systeem volledig te begrijpen (capaciteiten en beperkingen)
- Automatiseringsbias te herkennen en te weerstaan
- Output correct te interpreteren
- Te besluiten het systeem niet te gebruiken of output te negeren/terug te draaien
- Het systeem te onderbreken via een "stop"-knop of vergelijkbare procedure

### 6. Nauwkeurigheid, robuustheid en cyberbeveiliging (Art. 15)

| Eis | Detail |
|-----|--------|
| **Nauwkeurigheid** | Gepast niveau van nauwkeurigheid, robuustheid en cyberbeveiliging; consistente prestaties |
| **Robuustheid** | Weerbaar tegen fouten, foute of onverwachte input, en pogingen tot manipulatie |
| **Back-up plannen** | Fail-safe plannen voor technische kwetsbaarheden |
| **Cyberbeveiliging** | Bescherming tegen pogingen om het systeem te veranderen via 'data poisoning', adversarial examples, model poisoning, etc. |
| **Zelflerend** | Bij zelflerende systemen: specifieke maatregelen om bias-feedbackloops te voorkomen |

### 7. Registratie en incidentmelding (Art. 49, 62)

- Hoog-risico AI aanbieders registreren zich en hun systemen in de **EU-databank voor hoog-risico AI**
- **Ernstige incidenten** (dood, ernstige schade aan gezondheid/eigendom/grondrechten) melden aan markttoezichtautoriteit
- Meldtermijn: **binnen 15 dagen** na vaststelling (of onmiddellijk bij overlijden)
- **Gebruikersdeployers** moeten incidenten aan de aanbieder melden

## Verplichtingen voor beperkt-risico AI (Art. 50)

Transparantieverplichting voor AI-systemen die interacteren met natuurlijke personen:

| Systeem | Verplichting |
|---------|-------------|
| **Directe interactie met personen** | Natuurlijke personen informeren dat ze met een AI-systeem interacteren (tenzij duidelijk uit de context) |
| **Synthetische content** | Output van AI die audio, beeld, video of tekst genereert die op echte personen/content lijkt, moet als kunstmatig worden gemarkeerd |
| **Deepfakes** | Extra markeringseisen; vrijgave van bestaan deepfakes |
| **Emotieherkenning/biometrie** | Informeren over de werking van het systeem aan de blootgestelde personen |

## GPAI-modellen (Art. 51-55)

**Algemene AI-modellen met systemisch risico** (>10^25 FLOPs cumulatief):

- Modelevaluatie (inclusief adversarial testing)
- Risicobeoordeling en -beperking op EU-niveau
- Registratie in EU-databank
- Cybersecuritybescherming
- Energierapportage
- Gedocumenteerde trainingsdataset-samenvatting (incl. auteursrechtbeleid)

## Rollen en verantwoordelijkheden

| Rol | Definitie | Kernverplichtingen |
|-----|-----------|-------------------|
| **Aanbieder** (Art. 2(2)) | Ontwikkelt AI-systeem of laat ontwikkelen en brengt op de markt | Volledige compliance, CE-markering, conformiteitsverklaring, EU-databank registratie |
| **Gebruiksverantwoordelijke (deployer)** (Art. 2(4)) | Gebruikt AI-systeem in professionele context (niet particulier, niet de aanbieder) | Menselijk toezicht waarborgen, inputdata relevant en representatief houden, monitoring, incidenten melden, FRIA uitvoeren |
| **Importeur** (Art. 2(5)) | Brengt AI-systeem uit derde land op EU-markt | Verificatie dat aanbieder voldoet aan alle verplichtingen, naam en adres op systeem |
| **Distributeur** (Art. 2(6)) | Maakt AI-systeem beschikbaar op EU-markt (niet aanbieder, niet importeur) | Verificatie CE-markering en documentatie; niet beschikbaar stellen bij niet-compliance |
| **Gemachtigde** (Art. 2(3)) | Namens niet-EU aanbieder in de EU | Volledige compliance namens aanbieder; documentatie 10 jaar bewaren |

**Let op:** De gebruiksverantwoordelijke van een hoog-risico AI-systeem heeft de plicht tot het uitvoeren van een **Fundamental Rights Impact Assessment (FRIA)** volgens Art. 27.

## FRIA — Fundamental Rights Impact Assessment (Art. 27)

Gebruiksverantwoordelijken (deployers) van hoog-risico AI moeten:

| Stap | Vereiste |
|------|----------|
| 1. Procesbeschrijving | Het proces waarin het AI-systeem wordt gebruikt vastleggen |
| 2. Gebruiksperiode en frequentie | Periode en frequentie van AI-gebruik bepalen |
| 3. Getroffen personen | Categorieën van natuurlijke personen en groepen die geraakt kunnen worden |
| 4. Risico-analyse | Specifieke risico's voor grondrechten uit Art. 9 |
| 5. Menselijk toezicht | Te treffen maatregelen voor menselijk toezicht volgens instructies |
| 6. Mitigerende maatregelen | Te treffen maatregelen bij materialisatie van risico's |

FRIA-resultaten moeten aan de AI-autoriteit worden gemeld (via formulier).

**Uitzonderingen:** MKB-bedrijven (klein/micro); uitzondering geldt NIET voor overheidsinstanties, ook niet kleinere gemeenten!

## Gebruiksverantwoordelijke verplichtingen (Art. 26-27)

**Voor overheidsorganisaties die AI-systemen gebruiken:**

- [ ] **FRIA uitvoeren** voor elk hoog-risico AI-systeem (Art. 27)
- [ ] **Menselijk toezicht** toewijzen aan gekwalificeerde personen met autoriteit en competentie (Art. 26(1)-(3))
- [ ] **Inputdata** relevant en representatief houden voor beoogd gebruik (Art. 26(5))
- [ ] **Monitoring** van het AI-systeem op basis van de gebruiksinstructie (Art. 26(4))
- [ ] **Incidenten melden** aan de aanbieder en AI-autoriteit (Art. 26(6))
- [ ] **Logboeken bewaren** voor zover onder controle (Art. 26(8))
- [ ] **Registreren in EU-databank** bij gebruik van hoog-risico AI (Art. 26(7)) — specifiek voor overheidsinstanties en overheidsbedrijven!
- [ ] **Werknemers informeren** over AI-gebruik op de werkplek (Art. 26(9))

## AI Literacy (Art. 4)

**Nieuw sinds 2 februari 2025:** Iedereen die AI-systemen gebruikt of erop toezicht houdt moet **voldoende AI-geletterdheid** bezitten. Voor organisaties:

- Technisch personeel: modelbegrip, biasdetectie, outputvalidatie
- Management: risicobeoordeling, governance, compliance
- Eindgebruikers: transparantie, beperkingen, juiste interpretatie

## Toezicht en sancties

### Nationale AI-autoriteit

Elke lidstaat moet minimaal één nationale toezichthoudende autoriteit aanwijzen. In Nederland wordt dit naar verwachting een nieuwe AI-autoriteit (niet de AP).

**Bevoegdheden:** markttoezicht, documentatie opvragen, testen uitvoeren, systemen van de markt halen, sancties opleggen.

### Sancties (Art. 99)

| Overtreding | Maximale boete |
|------------|----------------|
| Verboden AI-praktijken | **€35 miljoen of 7%** van wereldwijde jaaromzet (hoogste) |
| Andere inbreuken op AI Act | **€15 miljoen of 3%** |
| Verstrekken van onjuiste informatie | **€7,5 miljoen of 1.5%** |
| Unierecht voor MKB/startups | Laagste van de twee bedragen |

### AI Regulatory Sandboxes (Art. 57-58)

Lidstaten moeten AI-regulatory sandboxes opzetten voor gecontroleerd testen van innovatieve AI. De nationale AI-autoriteit houdt toezicht en geeft begeleiding over compliance.

## Compliance checklist — Aanbieder hoog-risico AI

- [ ] **Risicoclassificatie** uitgevoerd en gedocumenteerd
- [ ] **Risicomanagementsysteem** geïmplementeerd (Art. 9)
- [ ] **Data governance** gecontroleerd op bias en representativiteit (Art. 10)
- [ ] **Technische documentatie** opgesteld volgens Annex IV (Art. 11)
- [ ] **Gebruiksinstructie** geschreven met alle verplichte elementen (Art. 13)
- [ ] **Menselijk toezicht** ontworpen in de interface (Art. 14)
- [ ] **Nauwkeurigheid en robuustheid** getest en gedocumenteerd (Art. 15)
- [ ] **Conformiteitsbeoordeling** uitgevoerd (Art. 43) — interne controle of notified body
- [ ] **EU-conformiteitsverklaring** opgesteld (Art. 47)
- [ ] **CE-markering** aangebracht (Art. 48)
- [ ] **Registratie in EU-databank** (Art. 49)
- [ ] **Kwaliteitsmanagementsysteem** geïmplementeerd (Art. 17)
- [ ] **Documentatie 10 jaar bewaren** (Art. 18)
- [ ] **Automatisch gegenereerde logs** (Art. 12)
- [ ] **Correctieve maatregelen** procedure ingericht (Art. 20)

## Compliance checklist — Gebruiksverantwoordelijke (overheid)

- [ ] **FRIA uitgevoerd** en gemeld aan AI-autoriteit (Art. 27)
- [ ] **Menselijk toezicht** toegewezen aan competente personen (Art. 26)
- [ ] **AI-geletterdheid** personeel geborgd (Art. 4)
- [ ] **Inputdata** representativiteit gecontroleerd
- [ ] **Monitoring** van systeemprestaties ingericht
- [ ] **Incidentmeldprocedure** ingericht (binnen 15 dagen)
- [ ] **Registratie in EU-databank** (overheidsinstanties verplicht)
- [ ] **Werknemers geïnformeerd** over AI-gebruik
- [ ] **Verwerkingsregister AVG** bijgewerkt met AI-componenten
- [ ] **DPIA** uitgevoerd waar AI persoonsgegevens verwerkt
- [ ] **BIO2** maatregelen verifieerd voor AI-systemen op overheidsinfrastructuur

## IAMA Integratie

Bij AI-systemen in overheidscontext moet ook het **IAMA** (Impact Assessment Mensenrechten en Algoritmes) worden doorlopen. De FRIA en IAMA overlappen:

| Aspect | FRIA (AI Act) | IAMA (NL) |
|--------|---------------|-----------|
| Doel | Grondrechten-effecten AI | Integrale algoritme-effecten |
| Reikwijdte | Hoog-risico AI only | Alle overheidsalgoritmen |
| Diepgang | Gebruik bij specifiek proces | Gehele levenscyclus |
| Verplicht | Ja, voor deployers | Ja, voor overheid |
| Meldplicht | Aan AI-autoriteit | Aan controller/eigenaar |

**Praktijkadvies:** Voer de IAMA uit als hoofdproces en documenteer FRIA-specifieke elementen apart — overlap is groot genoeg om niet dubbel te starten.

## Architectuur en open source

- [EU AI Act GitHub Tracker](https://github.com/nicknochnack-Archive/EU-AI-Act-Compliance-Checker)
- [AI Act Explorer](https://artificialintelligenceact.eu/ai-act-explorer/)
- AI systemen die als **vrije en open-source** worden vrijgegeven, vallen NIET onder de definitie van "in de handel brengen" tenzij ze als hoog-risico worden gebruikt. Maar: open-source GPAI-modellen moeten nog steeds voldoen aan transparantie- en auteursrechtvereisten.
