# EU AI Act — Reference

## Volledige wettekst structuur

De AI Act (Verordening 2024/1689) telt 180 overwegingen (recitals) en 113 artikelen in 13 titels:

```
TITEL I      Algemene bepalingen (Art. 1-4)
TITEL II     Verboden AI-praktijken (Art. 5)
TITEL III    Hoog-risico AI-systemen (Art. 6-49)
  HOOFDSTUK 1 Classificatie (Art. 6-7)
  HOOFDSTUK 2 Eisen (Art. 8-15)
  HOOFDSTUK 3 Verplichtingen aanbieders en gebruikers (Art. 16-27)
  HOOFDSTUK 4 Notified bodies (Art. 28-37)
  HOOFDSTUK 5 Normen, conformiteitsbeoordeling, certificaten (Art. 38-49)
TITEL IV     Transparantieverplichtingen (Art. 50)
TITEL V      GPAI-modellen (Art. 51-56)
TITEL VI     Innovatieondersteuning (Art. 57-58)
TITEL VII    Governance (Art. 59-71)
TITEL VIII   EU-databank voor hoog-risico AI (Art. 72)
TITEL IX     Post-market monitoring en informatie-uitwisseling (Art. 73-78)
TITEL X      Gedragscodes en richtsnoeren (Art. 79-80)
TITEL XI     Delegatie en uitvoering (Art. 81-84)
TITEL XII    Sancties (Art. 85-89)
TITEL XIII   Slotbepalingen (Art. 90-113)
```

## Annex overzicht

| Annex | Inhoud |
|-------|--------|
| **Annex I** | EU-harmonisatiewetgeving (productveiligheidslijn) — machines, speelgoed, medisch, liften, PED, radioapparatuur etc. |
| **Annex II** | Producten waarvoor derdepartij conformiteitsbeoordeling verplicht is |
| **Annex III** | Hoog-risico AI use cases (8 domeinen, zie SKILL.md) |
| **Annex IV** | Technische documentatie minimuminhoud |
| **Annex V** | EU-Conformiteitsverklaring template |
| **Annex VI** | Conformiteitsbeoordeling op basis van interne controle |
| **Annex VII** | Conformiteitsbeoordeling op basis van kwaliteitsmanagementsysteem + technische documentatie |
| **Annex VIII** | Bepalingen voor registratie in EU-databank |

## Relatie met andere EU-regelgeving

| Verordening | Raakvlak | Art. AI Act |
|------------|----------|-------------|
| **AVG (GDPR)** | Persoonsgegevens in training data en AI output; DPIA verplicht naast FRIA; recht op uitleg bij geautomatiseerde besluiten (Art. 22 AVG) | Art. 10(5), 26(9), 27 |
| **Data Act** | Toegang tot data voor AI-training; cloud switching bij AI-diensten | Art. 10 |
| **Cyber Resilience Act** | Cybersecurity-eisen voor producten met digitale elementen (incl. embedded AI); SBOM verplicht; overlap met AI Act Art. 15 | Art. 15 |
| **NIS2 / Cyberbeveiligingswet** | Cybersecurity van AI-infrastructuur; meldplicht incidenten; BIO2 = sectorale invulling | Art. 15 |
| **DSA (Digital Services Act)** | AI-aanbevelingssystemen op platforms; transparantieverplichtingen overlappen | Art. 50 |
| **Productaansprakelijkheidsrichtlijn** | Aansprakelijkheid voor schade veroorzaakt door AI-systemen | Art. 1, Preambule |

## NL-specifieke implementatie

### Tijdlijn

| Datum | Mijlpaal |
|-------|----------|
| **1 aug 2024** | AI Act van kracht |
| **2 feb 2025** | Verboden AI-praktijken + AI-geletterdheid van kracht |
| **H2 2025** | Verwachte aanwijzing NL AI-autoriteit |
| **2 aug 2025** | GPAI-model regels van kracht |
| **2 aug 2026** | Hoog-risico AI (Annex III) volledig van kracht |
| **Q4 2026** | Verwachte ingebruikname NL AI regulatory sandbox |
| **2 aug 2027** | Hoog-risico AI (Annex I productveiligheid) van kracht |

### NL governance structuur (verwacht)

```
Ministerie van BZK/EZ
  └── Nationale AI-autoriteit (nieuw op te richten)
      ├── Markttoezicht AI-systemen
      ├── EU-databank beheer
      ├── AI sandbox coördinatie
      └── Sanctiebevoegdheid
  ├── Autoriteit Persoonsgegevens (AVG/DGDP handhaving)
  ├── RDI (Rijksinspectie Digitale Infrastructuur) — CRA/NIS2
  └── Sectorale toezichthouders (AFM, DNB, NZa, etc.)
```

## Bronnen

- [EU AI Act full text (EUR-Lex)](https://eur-lex.europa.eu/legal-content/NL/TXT/?uri=CELEX:32024R1689)
- [AI Act Explorer](https://artificialintelligenceact.eu/ai-act-explorer/)
- [EU AI Act Compliance Checker (GitHub)](https://github.com/nicknochnack-Archive/EU-AI-Act-Compliance-Checker)
- [Future of Life — EU AI Act Summary](https://artificialintelligenceact.eu/high-level-summary/)
- [Digital Europe — AI Act Implementation](https://www.digitaleurope.org/resources/ai-act-implementation/)
- [Rijksoverheid — IAMA](https://www.rijksoverheid.nl/documenten/rapporten/2022/03/01/impact-assessment-mensenrechten-en-algoritmes-iama)
- [NORA — Algoritmes](https://www.noraonline.nl/wiki/Algoritme)
