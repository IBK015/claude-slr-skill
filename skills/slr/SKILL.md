---
name: slr
description: Plan, run, cross-check and write up a Systematic Literature Review (SLR) using the Wolfswinkel et al. (2013) Grounded Theory method, PRISMA 2020 reporting, and Gioia-style coding. Use whenever the user mentions SLR, systematic literature review, systematic review, literature review for a thesis or paper, PRISMA flow diagram, search string, Scopus or Web of Science search, inclusion/exclusion criteria, title and abstract screening, dual reviewers or cross-checking a screening sheet, coding literature, concept matrix, or writing the methodology section of a review, even if they do not say "systematic".
---

# SLR: Systematic Literature Review (PRISMA + Grounded Theory)

An SLR answers one question: **what do we know from the literature about a specific topic at the moment?** It is rigorous because every choice (question, sources, criteria, screening, coding) is explicit, justified and reproducible, which keeps the risk of bias low. This skill guides the user through the whole review, runs the screening and cross-checking, and drafts the artefacts a supervisor or reviewer expects.

The method stacks three well-established pieces:

| Layer | Source | Job |
|---|---|---|
| Process | Wolfswinkel, Furtmueller & Wilderom (2013), five stages and eleven steps (Table 1 of the paper): 1 Define (1.1 criteria, 1.2 fields, 1.3 sources, 1.4 search terms), 2 Search (2.1), 3 Select (3.1 refine the sample), 4 Analyze (4.1 open, 4.2 axial, 4.3 selective coding), 5 Present (5.1 represent and structure the content, 5.2 structure the article) | Overall workflow, used iteratively |
| Reporting | PRISMA 2020 (Page et al., 2021): flow diagram + 27-item checklist; PRISMA-S for search reporting | Transparency of identification, screening, inclusion |
| Analysis | Grounded-Theory coding as used by Wolfswinkel et al. (2013) and Gioia et al. (2013): open, axial, selective coding | Turning included papers into findings |

The choices here follow a University of Twente Change Leaders Honours SLR course guide (2025) and three example student SLRs that use this pattern. Treat that guide as the house style unless the user or their supervisor says otherwise. Wolfswinkel et al. say the method is a guide, not a straitjacket: deviation is fine when it is motivated and documented.

## Ground rules (why they matter)

1. **Never invent papers, counts, dates or database results.** Scopus and Web of Science sit behind licences, so Claude cannot run them. The user runs the search string and exports results (RIS, CSV, XLSX or BibTeX); Claude works from the export. Every PRISMA number must trace to a real export or a screening log. A fabricated number destroys the one property an SLR is for.
2. **Every criterion gets a justification.** "English only" is fine, but say why (all authors can read it, reviewers can check it).
3. **Keep a logbook from day one.** Wolfswinkel et al. recommend a process diary at every stage: each choice and its reason, dated. It makes the Present stage honest and lets steps be redone. Any revision (a relaxed criterion, an extra synonym, a sharpened RQ) means every later decision from that point must be reconsidered, so log the change and what must be redone.
4. **Iterate deliberately.** The RQ is seldom unchanged by the end. Searching shows missing synonyms and surprises; go back to Define, fix it, log it, and repeat the affected steps.
5. **Text, criteria, sheet and numbers must agree.** In past student SLRs the methodology said "journal articles only" while other text mentioned conference papers and book chapters, and the sheet showed values that the declared criteria did not address. Run the cross-checks below before delivering anything.
6. **Separate what the papers say from what you infer.** Findings must be attributable to specific included studies.
7. **Ask before big choices, assume for small ones.** If the session is interactive, use AskUserQuestion for the intake. If unattended, state assumptions at the top and proceed.

## Tools to use when present

- **Markitdown MCP** (`convert_to_markdown`), if installed: read PDFs of papers, guides and example SLRs. Large outputs are saved to a file; slice them with Python instead of re-reading. Otherwise use any PDF-to-text tool available.
- **The user's own sheets:** Excel Online and SharePoint sheets are drawn on a canvas, so browser tools cannot read the cells and often time out. Ask for a download (XLSX preferred) or a CSV per tab into the connected folder, then read it with Markitdown, pandas or openpyxl. Do not guess at its contents, and check every tab and hidden column.
- **Zotero MCP**: store the corpus, run `zotero_find_duplicates`, add records by DOI, tag by screening status, export the bibliography.
- **Elicit / Consensus / OpenAlex / Semantic Scholar**: scoping, pilot searches, seed papers, snowballing. Not a replacement for Scopus/WoS in the reported search; if used, report them as an additional source and count separately.
- **deep-research skill, `systematic-review` mode**: hand off, or borrow, for the PRISMA-P protocol template, PICOS question formulation, risk-of-bias tools and the PRISMA 2020 report template, especially for health or intervention reviews and meta-analyses. Narrative and thematic SLRs (the default here) run directly in this skill.
- **A writing-humanizer skill**, if the user has one or asks for it: run drafted prose through it last. Never on search strings, tables or counts.
- **xlsx / docx skills**: read the relevant SKILL.md before building deliverables. For spreadsheets recalculate and confirm zero formula errors.

## Step 0: Intake

Establish, skipping anything already known:

1. Purpose and audience: course assignment, master thesis chapter, journal paper, proposal.
2. Topic and a first draft of the RQ (Wolfswinkel: explicate the topic and scope, however vaguely, before starting).
3. Discipline and likely databases; access to Scopus / WoS / IEEE / PubMed.
4. Team size and who screens (drives the dual-screening design).
5. Length, deadline, format, citation style.
6. Constraints from the supervisor or guide (journal articles only, empirical only, English, IF threshold, years).
7. Existing SLRs on the topic (year threshold, search terms).
8. Any existing sheet, search export or PRISMA draft to build on.

Confirm a one-paragraph **review plan** before searching.

## Stage 1: Define (steps 1.1 to 1.4)

### 1a. Research question

- Use a **what/how** question, as specific as possible, simple. Example from the guide: *How does emotional intelligence influence conflict management in agile teams?* Sub-questions are welcome and later structure the results.
- Test it: answerable from empirical papers? Too broad (thousands of hits) or too narrow (under about 30)? Key concepts, population and context named?
- Frames: PICO(S) for intervention questions; PICo or SPIDER for qualitative work; Population/Context, Concept/technology, Outcome for engineering and planning. Write the frame in a small table.

### 1b. Criteria for inclusion and exclusion (step 1.1)

Produce a table: **Criterion | Decision | Justification | Where applied (DB filter / title-abstract / full text)**. Wolfswinkel counts non-content sampling criteria here too: outlet type, an impact-factor threshold, a time frame.

Typical, from the guide (adjust to the field and say so):

- Document type: peer-reviewed journal articles only (no book chapters, theses, conference proceedings). For computing, engineering and spatial fields, conference papers carry the state of the art; if included, say so and keep text and criteria aligned.
- Empirical papers only. Say what "empirical" means here; reviews may serve as background but not in the sample.
- Language: English.
- Field or subject area.
- Quality proxy: journal Impact Factor above 1 (the guide's example) or a Scimago quartile. **Decide explicitly whether it is applied.** IF is blunt and can exclude good work in small fields; if it is not applied, say so and do not present IF values as if they were screening evidence.
- Time window: the year of the last comparable SLR, or a defensible turning point.
- Topic-specific operational definitions: which synonyms of each construct count and which do not, decided before screening (the EI and well-being example spent a full subsection on this).
- RQ-specific exclusions (for example: studies on followers' gender when the RQ is about leaders' gender).

Split criteria into **database-level filters** (applied at search; PRISMA "records removed before screening") and **screening-level criteria** (applied by reading). Wolfswinkel: if the sampling were redone with the same criteria, the same results should surface.

### 1c. Fields (1.2) and sources (1.3)

- Name the research field(s); for interdisciplinary topics have team members who know each field.
- Default pair: **Scopus + Web of Science Core Collection**. Add discipline databases: PubMed/MEDLINE (health), PsycINFO (psychology, education), IEEE Xplore / ACM (computing), GreenFILE or GEOBASE (environment, geography), EconLit, ERIC. Justify each in a sentence.
- Two databases is the practical minimum; one only with an explicit limitation.
- Grey literature and reports for fast-moving applied topics: a clearly separated optional stream, never mixed into the peer-reviewed count.

### 1d. Search terms (1.4)

Terms reflect the whole scope of the chosen area. **All search terms used must be listed in the article.** Build them in Stage 2.

## Stage 2: Search (step 2.1)

### 2a. Build the string

1. Extract the **concepts** from the RQ (2 to 4 blocks).
2. For each block list synonyms, related terms, spelling variants, acronyms; harvest from seed papers, existing SLRs, thesauri.
3. **OR** inside a block, **AND** between blocks.
4. Truncation `*` for endings (`lead*` gives leader, leaders, leadership, leading); wildcard `?` for spelling variants (`organi?ation`); quotes for phrases.
5. Apply to **title, abstract, keywords** (Scopus `TITLE-ABS-KEY(...)`, WoS `TS=(...)`).

Guide example:
`(emotional intelligence OR emotion management OR emotion regulation*) AND (conflict management OR conflict* OR conflict dynamic*) AND (agile team* OR self-managing team* OR self-organi?* team*)`

**Search strings differ per database.** Field tags, wildcards, proximity operators and filters differ. Produce one translated string per database and say which syntax changed.

### 2b. Calibrate

- Expect "feast or famine" and surprises (Wolfswinkel). Start broad, then tighten; one example SLR deliberately used a broad two-block query.
- **Target: under about 1000 records after the first (filter) screen.** Above that, add a block or narrow a field; far below about 30, loosen synonyms.
- **Recall check:** the user names 3 to 5 papers that must be found; if the string misses them, fix the string.
- Run the same day in each database. Log database, date, exact string, filters, hits before and after each filter (Search_Log sheet).

### 2c. Export

RIS, CSV or BibTeX with abstracts, one file per database. Import into the workbook or Zotero. Never type counts from memory.

## Stage 3: Select (step 3.1), initial screening, PRISMA

Wolfswinkel's order for refining the sample:

1. **Filter out doubles.**
2. **Set aside papers that do not fit the criteria**, by reading titles, abstracts, or more of the text.
3. **Check forward and backward citations** of what is selected to enrich the sample.
4. **For every newly added article, run Stage 3 again**, going back and forth until no new relevant articles appear (the data are exhausted). Do not start citation tracking prematurely: it wastes effort on papers that end up excluded.
5. **Team reliability:** reviewers discuss criteria and reasons and settle on the final subset. Run an **inter-coder check with at least 90% overlap in article selection among at least two coders** (the standard Wolfswinkel et al. propose). Each reviewer builds their own **selection table** (Year, Author(s), Title, Journal, Reason(s) for its selection), ordered by year; compare tables and agree on the final set. Working alone, the table still explains why each paper was chosen.

### Initial screening protocol (title, abstract, keywords)

Use this whenever the user is starting or reviewing the first screening round.

1. **Prepare the sheet.** One row per record left after de-duplication and database filters, with ID, authors, year, title, journal, abstract, keywords. Reviewer columns are blind: A and B decide independently before looking at each other's. Sort by year or by ID, never by relevance score.
2. **Write operational rules first.** For each criterion and each key construct, a one-line decision rule with borderline examples. Put them in the Protocol and Logbook.
3. **Pilot / calibration.** Both reviewers screen the same first 20 to 30 records (or about 10%), compare, discuss every disagreement, sharpen the rules, log changes. Repeat once if agreement is below 90%.
4. **Decision codes.** `Include`, `Exclude`, `Maybe`. Be inclusive at this stage: when the abstract cannot settle a criterion, use `Maybe` and decide at full text. Every `Exclude` carries a coded reason (R-codes: not empirical, wrong document type, language, time, field, off topic, wrong population or actor, key construct missing, below quality threshold, not retrievable, other).
5. **Read in a fixed order** from cheap to expensive: document type, language, year, field; then topic relevance in title and keywords; then the abstract for population, construct(s), design, outcome.
6. **Compare and resolve.** Compute percent agreement and Cohen's kappa. Discuss each disagreement; if still unresolved, a third person decides. Nothing stays `Maybe` after the round: it moves to full text as `Include`, or is excluded with a reason.
7. **Workload options.** Best: both reviewers screen every record. Pragmatic, and common in student teams: split the records, then have a second reviewer check every `Include` and `Maybe` and a random sample (at least 20%) of the `Exclude` decisions, and report agreement on the overlap. The examples verified that every paper was seen by at least two people; say which design you used.
8. **Log** the counts, agreement, rule changes and who did what. Keep every screened record in the sheet with its decision and reason, including the excluded ones, and keep the same ID for a paper in every tab.
9. **Full-text round.** Retrieve reports (no licence or no author reply goes into "reports not retrieved" and is reported). Two reviewers read carefully, decide, and code every exclusion reason. Then do forward and backward citation on the included set and return to step 1 for any new candidates.

### PRISMA 2020 mapping and arithmetic

| PRISMA box | Source |
|---|---|
| Records identified from databases and registers (n, databases n) | Search_Log |
| Records identified from other methods | citation searching, other sources |
| Records removed before screening: duplicates; marked ineligible by filters; other reasons | Records, Search_Log |
| Records screened | TA_Screening rows |
| Records excluded | TA final = Exclude |
| Reports sought for retrieval / not retrieved | FT_Screening |
| Reports assessed for eligibility | sought minus not retrieved |
| Reports excluded with reasons (count per reason) | FT final = Exclude by R-code |
| Studies included in review | FT final = Include |

Arithmetic checks, run every time:

- identified from databases minus removed before screening = screened
- screened minus excluded (plus reports sought from other methods) = reports sought
- sought minus not retrieved = assessed
- assessed minus sum of reason counts = included
- database total = sum of per-database counts; duplicates cannot exceed the total.

Use the PRISMA 2020 labels and cite Page et al. (2021); older SLRs cite the four-phase Moher et al. (2009) model.

Worked check with a real student example (an SLR on leader gender and follower trust): 291 identified, 126 removed by filters, 165 screened, 145 excluded, 20 sought, 1 not retrieved, 19 assessed, 7 excluded (4 follower-gender studies, 2 not relevant, 1 no gender dimension), 12 included. Every step reconciles.

## The screening workbook and cross-checking

Use the bundled template `assets/SLR_Screening_Workbook_Template.xlsx` (regenerate it with `scripts/build_workbook.py <output.xlsx>` if needed); otherwise build the sheets with an xlsx skill. Sheets: **README, Protocol, Search_Log, Records, TA_Screening, FT_Screening, Reliability, PRISMA_Counts, PRISMA_Flow, Evidence_Table, Concept_Matrix, Logbook, Lists.** Key design points:

- Yellow cells are inputs, green cells are formulas; drop-downs for decisions and reason codes; example rows are grey and outside the counted range.
- `TA_Screening` and `FT_Screening` hold Reviewer A and B columns, an `Agree?` formula, a `Final decision` and a `Resolved by` field.
- `Reliability` computes percent agreement (flag below 90%) and Cohen's kappa over Include / Exclude / Maybe.
- `PRISMA_Counts` derives every flow number by formula and shows OK or MISMATCH next to each arithmetic check; `PRISMA_Flow` draws the diagram from those counts.
- `Evidence_Table` has the guide's columns; `Concept_Matrix` is Wolfswinkel's Table 3 and 4.

### Cross-check protocol

When the user shares a sheet or workbook, read **every tab** (export each as CSV or XLSX; hidden columns and extra tabs matter) and report a short table of findings (check, result, what to fix). Checks:

1. **Structure.** Each screening tab needs a stable **record ID**, authors, year, title, journal, DOI or link, the search date, and per-reviewer decision plus a coded reason. Missing year or journal columns block de-duplication and quality checks. Authors in one format; abstracts complete, without stray line breaks.
2. **Stable IDs across tabs.** The same paper must keep the same ID in every tab. If a shortlist is renumbered (1 to 12) after a longer list (1 to 20), cross-referencing becomes error-prone; carry the original ID or DOI.
3. **Decision recorded, not inferred.** There should be an explicit Include / Exclude column. If inclusion can only be inferred (a blank comment, or an IF value present), say so and ask the team to add the column. A free-text Comments column with a person's name in it is not a decision or a reviewer field.
4. **Controlled reasons.** Free-text comments ("Not on leadership", "Focussed on follower gender influence", "Not relevant") describe the same PRISMA reason in different words. Map each to one R-code so PRISMA counts per reason are countable.
5. **Every screening stage is logged.** PRISMA needs the records screened and the number excluded at title and abstract stage. A tab that holds only the papers that survived (for example 20) makes the earlier step (for example 165 to 20) unverifiable. Keep all screened records with a decision, even the excluded ones.
6. **Criteria versus data.** Test each declared criterion against the columns present. If an IF threshold is not declared, an IF column that is filled only for the included papers signals that IF was collected after selection and is informational; if it is declared, count rows below it.
7. **Query versus counts.** If the search string embeds filters (for example `AND PUBYEAR > 2018 AND PUBYEAR < 2027`), the reported "records identified" and "removed by filters" must match how the string was actually run. Ask for the hit count with and without the embedded filters, the date, and the interface.
8. **Row counts and reasons.** Rows per tab versus the sample sizes in the text and PRISMA; the reason counts must sum to the number excluded.
9. **Document type.** Spot-check that the sheet respects the document-type criterion (for example a title ending "An Abstract" with a book-series DOI is a conference or book-chapter abstract, not a journal article).
10. **Dual-review agreement.** Compute agreement and kappa; list every disagreement and its resolution.
11. **Relevance spot-check.** For each included row, does the title and abstract meet the RQ? Ask for the "why it matters for the RQ" sentence for doubtful ones.
12. **Sheet versus paper.** Every included paper appears in the text, the evidence table and the reference list; no cited study is missing from the sheet.
13. **Export hygiene.** CSV exports can lose non-ASCII characters (curly apostrophes and hyphens become `?` or a replacement character). Ask for XLSX or UTF-8 with BOM, then fix titles before they go into the reference list.

**Worked example: an anonymised student team workbook (leader gender and follower trust), three tabs.** The RQ and Query tab holds the RQ and the Scopus string with the 2019 to 2026 year clause embedded. The Scopus tab lists 20 full-text candidates with a Comments column. The Sheet1 tab lists the 12 included papers. What the cross-check found:

- The counts reconcile with the paper: 20 read in full, 1 with no access, 19 assessed, 7 excluded, 12 included. The seven reasons match the paper (four follower-gender studies, two not relevant, one no gender dimension), though the comments word them inconsistently.
- Included papers keep no persistent ID: Sheet1 renumbers them 1 to 12 while the Scopus tab numbers them 1 to 20 (for example one paper is 7 in one tab and 9 in the other).
- There is no decision column and no reviewer column; the Date column is empty; one Comments cell holds a name rather than a reason.
- The 165 records screened at title and abstract stage, and the 145 excluded, are not in the workbook, so that step cannot be traced.
- IF is filled only for the 12 included papers; six of them are below 1 (0.11 to 0.77). The declared criteria (English, articles, 2019 to 2026) do not include an IF filter, so state that IF is informational.
- The query in the sheet embeds the year clause, while the paper's methodology prints the query without it and applies the period as a later criterion (291 to 165). Confirm which count the 291 refers to.
- One of the 20 (a Springer book-series abstract) looks like a non-journal item that reached full-text stage, which suggests the document-type filter was not applied in the database.
- Export encoding replaced some characters in titles.

## Stage 4: Extract and appraise

Build the **evidence table**, one row per included paper. Columns from the guide:

- Authors (year), Title, Journal
- Summary (2 to 4 sentences)
- Details: context/country, sample, design (qualitative / quantitative / mixed), theory or model, measures, key results, and whether the study **agrees with or departs from** others
- **Why it matters for the RQ**: one sentence. If it cannot be written, the paper probably should not be included.

Useful extras: aims, methodology, limitations or biases, constructs and definitions, mediators and moderators, keywords. Optional quality appraisal (CASP, JBI, MMAT); if not performed, say so as a limitation. Report the sample profile: year distribution, countries, designs (for example "14 quantitative, 4 qualitative, 1 mixed"), journals.

## Stage 5: Analyze (steps 4.1 to 4.3, Grounded Theory)

This is the heart of the review. Wolfswinkel et al. use the Strauss and Corbin stream; the guide maps it to Gioia et al. (2013).

**Excerpting.** Pick a random paper, read, and highlight every finding or insight relevant to the scope and RQ. Every selected paper is highlighted at least once. Each highlighted passage is an excerpt; record which paper it belongs to. Sub-grouping papers before analysis needs a subject-matter reason and an explicit write-up of how the subsets are linked later.

| Step | What you do | Gioia term |
|---|---|---|
| **Open coding** | Re-read excerpts, name **concepts** that capture them and their properties; add meta-insights on method and theory. The first abstraction step; revisit earlier papers when a later paper changes a concept's properties | 1st-order concepts |
| **Axial coding** | Group concepts into **categories and sub-categories**, and work out how they relate, including properties | 2nd-order themes |
| **Selective coding** | Integrate and refine: develop the relations between the **main categories** that concern the subject or RQ, and build one reasoning that explains the phenomenon | Aggregate dimensions |

How to work:

1. **Constant comparison.** The three steps are intertwined. Keep comparing categories against papers and excerpts, and revise.
2. **Theoretical sampling.** Preliminary results from the first papers guide how the remaining papers are read and where more data are needed.
3. **Saturation.** Continue until no new concepts, properties or interesting links arise. Saturation is debatable and limited by time; say honestly whether it was reached.
4. **Documentation.** Keep a dated codebook with memos (`code | definition | example excerpt | paper IDs | date`). Wolfswinkel suggests separate books for (a) coding, (b) evolving theory, (c) methodological or research-area issues noticed on the way.
5. **Concept matrix.** Papers as rows, concepts as columns (Tables 3 and 4). As papers are added, concepts are merged (X and Y become XY), split (W into U and V) or relabelled, and earlier papers are re-checked. Log every change.
6. **Induction and deduction** can be combined; codes both inspire and verify. Not all original variables need to resurface: a review may show that a variable needs enrichment or less attention.
7. **Small samples** (about 12 papers) may not support full axial and selective coding. Say so and apply open coding with categories, as one example did.
8. **Gaps and conflicts** between studies become the discussion and future-research agenda.

Ground every claim with its supporting studies, e.g. (Author, Year).

## Stage 6: Present (steps 5.1 and 5.2)

- Represent and structure the content from the findings and insights in the logbooks. Results by **sub-RQ** or around the **storyline** from selective coding.
- Include a solid account of the empirical facts for readers who only want an overview, and give a rationale for any additional representation.
- Use visuals: the guide encourages your own model; Wolfswinkel cites concept-centric versus author-centric listings, concept matrices, and diagrams showing conceptual overlap (for example circles sized by number of concepts or papers per category). Show more than a passive list of concepts.
- Be transparent: disclose the key choices from the logbook, including changes to criteria and RQ.
- Balance the creativity of the data against the creativity of the reviewer; state your prior beliefs.
- Discussion: answer to the RQ, agreement or conflict with earlier work, implications, **limitations** (databases, language, quality filter, sample size, screening reliability), future research.

Order that works: overview of included studies; findings by theme with a "so what" line; integrative model; discussion; short conclusion. Appendices: search strings with dates, PRISMA diagram, exclusion list, evidence table, codebook.

## Methodology section template

Fill from the logbook and workbook; never from memory.

```
2. Methodology
2.1 Research design and process
   Grounded-theory literature review method (Wolfswinkel et al., 2013), five stages;
   PRISMA 2020 for reporting (Page et al., 2021); why this fits the RQ.
2.1.1 Search strategy
   Databases and why; fields searched; how keywords were derived; the full query in a
   code block; date of search; records retrieved per database.
2.1.2 Inclusion and exclusion criteria
   Numbered list, one justification per criterion; counts after each filter
   (e.g. 291 to 165) or reference to the PRISMA figure. State whether an IF threshold was used.
2.1.3 Study selection
   Who screened what; title/abstract stage; full-text stage; cross-verification and agreement
   (at least 90% overlap; kappa); inaccessible papers; exclusion reasons; final sample size;
   pointer to the evidence table.
2.2 Data analysis
   Excerpting, open, axial, selective coding; who coded; disagreement handling; saturation;
   tools; figure or table of the coding structure.
Figure 1. PRISMA 2020 flow diagram.
```

Style: past tense, precise numbers, every filter explained. Run drafted prose through a humanizer pass if the user wants one.

## QA checklist before delivering

Run and report each check:

- [ ] RQ identical in title, abstract, methodology, conclusion.
- [ ] Criteria in the text equal the criteria applied in filters, sheet and PRISMA (document type, language, years, subject area, IF).
- [ ] Every number in the text matches the PRISMA diagram; all arithmetic checks hold.
- [ ] Every full-text exclusion has a coded reason and the reasons sum correctly.
- [ ] Agreement between reviewers computed and at least 90% (or the shortfall explained and rules recalibrated).
- [ ] Search strings verbatim with database, date and hit count; all search terms listed.
- [ ] Each included paper is in the evidence table, the concept matrix and the results.
- [ ] No claim in the results without a citation to an included study.
- [ ] Logbook covers every change to RQ, criteria and strings.
- [ ] Limitations mention databases, language, quality filter, sample size, screening reliability.
- [ ] References verified (DOI resolves, author and year correct); Zotero or Crossref when available.
- [ ] PRISMA 2020 checklist walked through (title; abstract; rationale; objectives; eligibility; sources; search; selection; data collection and items; appraisal; synthesis methods; study selection and characteristics; synthesis results; discussion; limitations; registration; support; competing interests; data availability). Mark items that do not apply to narrative SLRs (effect measures, certainty grading) as such.
- [ ] Prose polished (humanizer pass if requested); tables, strings and counts untouched.

## Deliverables (offer what the user needs)

1. **Review plan / protocol** (1 to 2 pages).
2. **Search pack**: one string per database, syntax notes, test-paper checklist.
3. **Screening workbook** (the template above) with real counts and live checks.
4. **PRISMA 2020 flow diagram** from real counts.
5. **Cross-check report**: the findings table from the protocol above.
6. **Evidence table, concept matrix, codebook, data-structure figure.**
7. **Methodology, results, discussion drafts** in the user's format.

Work in phases and let the user approve each: plan, strings, screening, extraction, coding, write-up. If a phase reveals a problem, go back a stage, fix it, and log the change.

## Adapting to other fields

- **Thesis in geoinformation, planning or engineering** (for example digital twins): add IEEE Xplore, ScienceDirect or Scopus subject filters for Earth and Planetary Sciences, Engineering, Environmental Science; consider conference papers and technical reports as a labelled second stream; define technology terms precisely (a digital twin is not any 3D model); expect heterogeneous designs that need a typology, not effect sizes.
- **Health or intervention reviews:** PICOS, protocol registration (PROSPERO or OSF), dual independent screening, formal risk of bias, optionally meta-analysis. Hand off to the deep-research skill.
- **Software engineering:** Kitchenham and Charters guidelines; the search and PRISMA steps still apply.
- **Fast timelines:** a rapid review is legitimate if declared, with shortcuts (one database, single screener, limited years) named as limitations.

## References to cite

- Wolfswinkel, J. F., Furtmueller, E., & Wilderom, C. P. M. (2013). Using grounded theory as a method for rigorously reviewing literature. *European Journal of Information Systems, 22*(1), 45-55.
- Page, M. J., et al. (2021). The PRISMA 2020 statement: an updated guideline for reporting systematic reviews. *BMJ, 372*, n71.
- Gioia, D. A., Corley, K. G., & Hamilton, A. L. (2013). Seeking qualitative rigor in inductive research. *Organizational Research Methods, 16*(1), 15-31.
- Webster, J., & Watson, R. T. (2002). Analyzing the past to prepare for the future: writing a literature review. *MIS Quarterly, 26*(2), xiii-xxiii.
- Strauss, A., & Corbin, J. (1990, 1998). *Basics of qualitative research.* Sage.
- Rethlefsen, M. L., et al. (2021). PRISMA-S: an extension to PRISMA for reporting literature searches. *Systematic Reviews, 10*, 39.
- Moher, D., et al. (2009). Preferred reporting items for systematic reviews and meta-analyses: the PRISMA statement.
- Landis, J. R., & Koch, G. G. (1977). The measurement of observer agreement for categorical data. *Biometrics, 33*(1), 159-174.
