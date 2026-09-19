# claude-slr-skill

A skill for [Claude](https://claude.ai) that guides you through a **Systematic Literature Review (SLR)**: from research question to search strings, screening, PRISMA flow diagram, coding and the methodology section. It works for a master thesis, a course assignment or a journal paper, in any discipline.

**What it combines**

| Layer | Source |
|---|---|
| Process: Define, Search, Select, Analyze, Present | Wolfswinkel, Furtmueller & Wilderom (2013), grounded-theory literature review method |
| Reporting: flow diagram and checklist | PRISMA 2020 (Page et al., 2021), PRISMA-S for search reporting |
| Analysis: open, axial, selective coding | Wolfswinkel et al. (2013) with the Gioia et al. (2013) first-order / second-order / aggregate terms |

## What is inside

```
skills/slr/
  SKILL.md                                   the skill (instructions Claude follows)
  assets/SLR_Screening_Workbook_Template.xlsx  dual-reviewer screening workbook with live PRISMA counts
  scripts/build_workbook.py                  regenerates the workbook template
```

The skill covers:

- research question and inclusion/exclusion criteria with a justification for each
- search strings per database (Scopus, Web of Science, PubMed, IEEE and others) with syntax notes
- an **initial screening protocol** (title, abstract, keywords): blind dual review, Include / Exclude / Maybe codes, coded exclusion reasons, pilot round, agreement of at least 90% (Wolfswinkel) plus Cohen's kappa
- a **cross-check protocol** for a team's screening sheet: IDs, decisions, reasons, criteria versus data, query versus counts, PRISMA arithmetic, sheet versus paper
- PRISMA 2020 flow numbers and arithmetic checks
- evidence table, concept matrix, codebook, grounded-theory analysis and how to present results
- a methodology-section template and a QA checklist

The workbook has sheets for the protocol, search log, records, title/abstract and full-text screening (two reviewers), reliability, PRISMA counts with OK / MISMATCH checks, a PRISMA flow diagram driven by formulas, an evidence table, a concept matrix and a logbook.

## Install

**Claude.ai (Pro, Max, Team, Enterprise) and Claude desktop / Cowork**

1. Download `slr.zip` from the [latest release](../../releases/latest).
2. In Claude, open the Skills settings and upload the zip.
3. Start a chat and turn the skill on.

**Claude Code**

```bash
git clone https://github.com/IBK015/claude-slr-skill.git
cp -r claude-slr-skill/skills/slr ~/.claude/skills/slr        # personal, all projects
# or: cp -r claude-slr-skill/skills/slr .claude/skills/slr    # one project only
```

Menu names change between Claude versions; if you cannot find the upload option, see Anthropic's documentation on Agent Skills.

## Use

Try prompts such as:

- "Use the SLR skill to plan a systematic literature review on *your topic*. Ask me what you need."
- "Build Scopus and Web of Science search strings for this research question: ..."
- "Here is our screening sheet. Cross-check it against our criteria and PRISMA numbers."
- "Draft the methodology section from our search log and screening workbook."

## What it does not do

- **It cannot search Scopus or Web of Science for you.** Those need your licence. You run the string, export the results (RIS, CSV, XLSX) and hand them over. The skill is written so that Claude never invents papers, counts or dates; every PRISMA number must come from your exports and logs.
- It does not replace your supervisor, a librarian or the reporting rules of your target journal. For health or intervention reviews with meta-analysis, use a dedicated protocol and registration route.
- Claude can make mistakes. Check references (DOIs, authors, years) and every number before you submit.

## Background and credit

The skill was drafted with Claude and checked against the Wolfswinkel et al. (2013) article, PRISMA 2020, and a University of Twente Change Leaders Honours SLR course guide (2025) with three example student SLRs. None of that course material or the articles are included here; please read the originals:

- Wolfswinkel, J. F., Furtmueller, E., & Wilderom, C. P. M. (2013). Using grounded theory as a method for rigorously reviewing literature. *European Journal of Information Systems, 22*(1), 45-55.
- Page, M. J., et al. (2021). The PRISMA 2020 statement: an updated guideline for reporting systematic reviews. *BMJ, 372*, n71.
- Gioia, D. A., Corley, K. G., & Hamilton, A. L. (2013). Seeking qualitative rigor in inductive research. *Organizational Research Methods, 16*(1), 15-31.
- Rethlefsen, M. L., et al. (2021). PRISMA-S: an extension to PRISMA for reporting literature searches. *Systematic Reviews, 10*, 39.

## Contribute

Issues and pull requests are welcome: field-specific search databases, screening rules, translations, and corrections to the method. Please describe the source for any methodological change.

## License

MIT, see [LICENSE](LICENSE). If the skill helps your work, you can cite it with [CITATION.cff](CITATION.cff).
