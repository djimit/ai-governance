# Copilot Instructions — ai-governance

> See root `.github/copilot-instructions.md` for global conventions.

Claude Code plugin voor **EU AI Act compliance**. Classificeert AI-systemen in risicocategorieën, checkt verplichte documentatie (technische documentatie, conformiteitsbeoordeling, risicomanagement), en adviseert over governance-structuren voor hoog-risico AI-systemen.

## Structure

```
.claude-plugin/plugin.json    # Plugin metadata (name, description, version, keywords)
skills/ai-governance/
  SKILL.md                    # Skill definition — triggers, model config, scope
  reference.md                # Reference material — EU AI Artikelen, risicocategorieën
```

## Installation

```bash
claude install djimit/ai-governance
```

## Typical Usage

- **Risicoclassificatie** — Bepaal of een AI-systeem verboden, hoog-risico, beperkt risico of minimaal risico is (Art. 5-7 EU AI Act)
- **Conformiteitsbeoordeling** — Genereer checklists voor technische documentatie, FRIA, kwaliteitsmanagement
- **Governance-advies** — Adviseer over menselijk toezicht, transparantie, bias-detectie
- **IAMA / NORA-integratie** — Koppel AI Act-eisen aan bestaande overheidskaders

## Domain Context

- EU AI Act (Verordening 2024/1689), van kracht sinds 1 augustus 2024
- Gefaseerde inwerkingtreding: Art. 5 (verbod) vanaf feb 2025, hoog-risico vanaf aug 2026
- Nederlandse context: BIO2, IAMA, NORA, AP-richtlijnen

## License

MIT (see `plugin.json`)
