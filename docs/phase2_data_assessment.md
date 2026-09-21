# Phase 2 — Data Acquisition and Dataset Assessment

## 1. Purpose

This document records the data-source selection, analytical population, coverage assessment, known limitations, and methodological decisions established during Phase 2 of the **Pokémon Competitive Meta Analytics** project.

Phase 2 is intended to confirm that the available data can support the analytical requirements defined in `AGENTS.md` before any final database schema, SQL transformation layer, Power BI model, or DAX logic is designed.

---

## 2. Primary Data Source

### VGC History

**Primary source:** VGC History  
**Website:** https://vgchistory.com/  
**Master dataset:** https://vgchistory.com/data.js  
**Sitemap:** https://vgchistory.com/sitemap.xml

The project uses VGC History as the primary analytical source because it provides structured tournament information suitable for reproducible BI analysis.

The locally cached `data.js` snapshot exposes structured objects including:

- `TOURNAMENTS`
- `PLAYERS`
- `MONS`
- `SEASONS`
- `REGS`
- `RULESETS`
- `GAMES`

The source also provides tournament-level standings, usage information, team-sheet coverage indicators, and match coverage metadata.

The project caches the source locally rather than repeatedly requesting it during analysis.

---

## 3. Source Freshness Validation

A fresh copy of `data.js` was downloaded with cache-bypass headers and compared with the original locally cached copy.

Both files had:

- identical file size;
- identical SHA-256 hash;
- identical tournament count;
- identical Worlds 2026 coverage values;
- identical NAIC 2026 coverage values.

Therefore, the original local `data.js` snapshot is considered the canonical Phase 2 source snapshot.

At the time of validation, the dataset contained:

**428 tournament records across all seasons and divisions.**

---

## 4. Selected Analytical Population

Version 1 of the project will focus on:

- **Championship Season:** 2026
- **Division:** Masters
- **Competitive circuit:** Pokémon Video Game Championships (VGC)
- **Included event tiers:** Regionals, Special Events, International Championships, and Worlds

The season field supplied by the source is used instead of inferring the Championship Series season from tournament names or calendar year.

This distinction is important because Championship seasons can contain events held during the preceding calendar year.

---

## 5. 2026 Masters Tournament Population

The selected population contains:

| Event Tier | Tournament Count |
|---|---:|
| Regional Championships | 26 |
| Special Events | 6 |
| International Championships | 3 |
| World Championships | 1 |
| **Total** | **36** |

All 36 selected records have:

- `season = 2026`;
- `division = Masters`;
- verified tournament records.

---

## 6. Regulation Coverage

The 2026 Masters population spans five regulations:

| Regulation | Tournament Count |
|---|---:|
| Regulation H | 12 |
| Regulation F | 12 |
| Regulation I | 8 |
| Regulation M-A | 3 |
| Regulation M-B | 1 |
| **Total** | **36** |

These regulation changes provide sufficient variation for the planned Meta Trends and tournament-comparison analyses.

Regulations must remain separate analytical categories and must not be combined without context.

---

## 7. Game Coverage

The 36 events are divided between two competitive game environments:

| Game | Tournament Count |
|---|---:|
| Scarlet & Violet | 32 |
| Pokémon Champions | 4 |
| **Total** | **36** |

The game transition must be preserved in the analytical model because it represents a meaningful competitive-environment change.

Game and regulation must not be treated as interchangeable fields.

---

## 8. Available Analytical Components

All 36 selected tournaments contain the four primary analytical components required by the project:

- usage data;
- standings data;
- team-sheet data;
- match data.

No tournament in the selected population is entirely missing any of these four components.

All 36 tournament records are also marked as verified by the source.

This means the complete 2026 Masters population can remain available for the project rather than being globally excluded based on missing analytical components.

---

## 9. Standings Coverage

### Standings Type

The 36 tournaments contain:

| Standings Type | Count |
|---|---:|
| Final | 35 |
| Swiss | 1 |
| **Total** | **36** |

The only tournament whose standings are marked as `swiss` rather than `final` is:

**Buenos Aires Special Event 2026**

Its source metadata reports:

- Tier: Special Event
- Regulation: H
- Reported players: 93
- Standings kind: Swiss
- Full standings flag: false
- Standings rows: 93
- Known team sheets: 94
- Match rows: 327

Because the event does not contain final standings, it may require special treatment for metrics that depend on final placement or top-cut outcomes.

It should not be removed from analyses that can be supported by its available usage, match, and Swiss-stage data.

---

## 10. Full-Standings Flags

Across the 36 events:

| Full Standings Flag | Count |
|---|---:|
| True | 21 |
| False | 15 |
| **Total** | **36** |

A `false` value does not automatically cause an event to be excluded.

Instead, actual row coverage and the requirements of each analytical metric must determine whether the event is usable for that metric.

---

## 11. Standings Coverage Findings

The lowest observed standings coverage percentages were:

| Tournament | Standings Coverage |
|---|---:|
| Los Angeles Regionals 2026 | 99.26% |
| Seville Special Event 2026 | 99.50% |
| Querétaro Regionals 2026 | 99.63% |
| Sydney Regionals 2026 | 99.64% |
| Monterrey Regionals 2026 | 99.65% |

Standings coverage is therefore extremely high across the selected population.

However, source discrepancies must remain visible rather than being manually corrected.

---

## 12. Team-Sheet Coverage Findings

Team-sheet coverage is also high across most tournaments.

The lowest observed team-sheet coverage percentages were:

| Tournament | Team-Sheet Coverage |
|---|---:|
| Auckland Special Event 2026 | 88.37% |
| Seville Special Event 2026 | 98.15% |
| Santiago Regionals 2026 | 98.60% |
| Birmingham Regionals 2026 | 98.84% |
| Querétaro Regionals 2026 | 98.89% |

Auckland is the clear low-coverage outlier for team sheets.

This does not automatically require exclusion.

Instead, Pokémon usage for Auckland must be interpreted as usage among the **known team sheets**, not among all reported tournament participants.

---

## 13. Match Coverage Findings

The lowest observed match-player coverage percentages were:

| Tournament | Match-Player Coverage |
|---|---:|
| Seville Special Event 2026 | 98.15% |
| Monterrey Regionals 2026 | 98.58% |
| Santiago Regionals 2026 | 98.60% |
| Querétaro Regionals 2026 | 98.89% |
| Buenos Aires Special Event 2026 | 98.92% |

Match coverage remains high across the selected population.

Match-based metrics must use only recorded match data rather than assuming every published participant has complete match coverage.

---

## 14. Source Count Discrepancies

Two records were identified where calculated coverage exceeded 100%.

### Turin Special Event 2026

The source reports:

- Reported players: 940
- Standings rows: 941
- Standings coverage: 100.11%
- Known team sheets: 940
- Match players: 940

The source also explicitly records a standings conflict:

- field = 940
- rows = 941
- delta = +1

No value will be manually overwritten.

---

### Buenos Aires Special Event 2026

The source reports:

- Reported players: 93
- Standings rows: 93
- Known team sheets: 94
- Team-sheet coverage: 101.08%
- Match players: 92
- Match-player coverage: 98.92%

The team-sheet count therefore exceeds the published player count by one.

This discrepancy will be retained as a data-quality flag rather than manually corrected.

---

## 15. Player Count Reliability

All 36 selected tournaments have:

`playersApprox = false`

Therefore, no selected tournament is explicitly marked by the source as having an approximate player count.

This does not eliminate the possibility of source inconsistencies, but it means the published player-count field is intended to represent an exact value according to the source metadata.

---

## 16. KPI-Specific Denominator Rules

The project will not use one universal denominator for every KPI.

Each measure must use the population that corresponds to the available underlying data.

### Pokémon Usage Rate

Usage must be calculated using known team sheets:

`Usage Rate = Teams containing Pokémon / Known team sheets`

Reported tournament attendance must not automatically be used as the usage denominator.

This avoids treating missing team sheets as if the Pokémon composition of those teams were known.

---

### Tournament Player Count

The tournament metadata `players` value will be used for published field size.

This measure describes reported tournament participation and is separate from standings, team-sheet, and match coverage.

---

### Placement Metrics

Placement analysis must use available standings records.

Events with incomplete or non-final standings must be appropriately flagged when calculating metrics such as:

- average placement;
- top-cut appearances;
- top-cut rate.

Buenos Aires Special Event 2026 requires special handling because its standings kind is `swiss`.

---

### Match Performance

Match-performance metrics must be calculated from available recorded matches.

The project must not assume that a participant without complete match records has an observed match result.

Match win rate therefore describes performance within the recorded match dataset.

---

## 17. Inclusion Strategy

The project will use **KPI-specific analytical eligibility** rather than an arbitrary global completeness threshold.

An event will not be excluded from the entire project simply because one analytical component is incomplete.

Instead:

| Analysis | Required Data |
|---|---|
| Tournament count | Tournament metadata |
| Player count | Reported player metadata |
| Pokémon usage | Known team sheets and team Pokémon |
| Usage trend | Comparable tournament usage data |
| Average placement | Appropriate standings and team data |
| Top-cut analysis | Final/top-cut-compatible standings and team data |
| Match win rate | Match records and team linkage |
| Regulation comparison | Regulation metadata and relevant metric data |
| Tournament comparison | Fields required by the selected comparison |

This approach preserves as much valid information as possible while preventing unsupported calculations.

---

## 18. Data Grain Observations

Phase 2 confirms that the source contains multiple possible analytical grains.

Observed structures include:

### Tournament Level

One record per tournament.

Includes metadata such as:

- tournament ID;
- name;
- dates;
- season;
- regulation;
- game;
- tier;
- division;
- player count;
- coverage indicators.

### Standing / Player-Tournament Level

Tournament standings contain player-specific information including:

- placement;
- player identifier;
- competitive record;
- registered team;
- verification indicators.

### Player-Tournament-Pokémon Level

Registered tournament teams can be normalized into one row per:

**Tournament × Player × Pokémon**

This is a strong candidate analytical grain for team and Pokémon-performance analysis.

### Match Level

Match records support match-based performance analysis at approximately:

**Tournament × Match**

The final fact-table architecture is **not locked in Phase 2**.

The final grain and dimensional model will be determined during Phase 4 after the raw data has been explored and cleaned.

---

## 19. Primary and Secondary Sources

### Primary Analytical Source

**VGC History**

Used for:

- tournament metadata;
- Championship season;
- regulation;
- game;
- event tier;
- player counts;
- standings;
- teams;
- tournament usage;
- coverage metadata;
- match data.

### Validation Sources

Where necessary, important tournament metadata or discrepancies may be cross-checked against:

- official Pokémon / Play! Pokémon sources;
- Limitless VGC.

These validation sources do not automatically replace the primary source.

Any reconciliation must be explicitly documented.

### Optional Contextual Source

Pokémon Showdown / Smogon-derived datasets such as PokéKit may be considered later for clearly separated contextual analysis or Pokémon metadata.

Ladder statistics must not be silently combined with official tournament statistics.

---

## 20. Known Limitations

Current known limitations include:

1. Some tournament standings are not flagged as fully complete.
2. Team-sheet coverage varies by tournament.
3. Match coverage varies slightly by tournament.
4. Auckland Special Event has materially lower team-sheet coverage than the other selected events.
5. Turin contains one more standings row than its reported player count.
6. Buenos Aires contains one more known team sheet than its reported player count.
7. Buenos Aires contains Swiss standings rather than final standings.
8. Recorded match performance may not represent every reported participant at every event.
9. Tournament participation, team-sheet coverage, standings coverage, and match coverage are distinct populations.
10. Association between Pokémon usage and performance must not be interpreted as proof that Pokémon choice alone caused tournament success.

These limitations must be retained in later methodology and dashboard documentation.

---

## 21. Phase 2 Decisions

The following decisions are now considered established for Version 1:

- Primary source: VGC History.
- Championship season: 2026.
- Division: Masters.
- Selected tournament population: 36 events.
- Included tiers: Regional, Special, International, Worlds.
- Regulations retained separately: H, F, I, M-A, M-B.
- Game retained as a separate analytical attribute.
- All 36 verified events remain in the overall analytical population.
- No global percentage threshold will automatically remove tournaments.
- Analytical eligibility will be KPI-specific.
- Pokémon usage will use known team sheets as its denominator.
- Source discrepancies will be flagged rather than manually corrected.
- Ladder and official tournament statistics will not be mixed without explicit labeling and methodological justification.
- The final fact-table schema remains unlocked until Phase 4.
- The Performance Index formula remains unlocked until later analysis supports an appropriate definition.

---

## 22. Phase 2 Outcome

Phase 2 confirms that the selected source provides sufficient data to support the planned Version 1 analytical scope defined in `AGENTS.md`.

The available data supports continued development of:

- Meta Overview;
- Meta Trends;
- Pokémon Performance;
- Pokémon Deep Dive;
- Tournament Analysis;
- Analytical Findings.

No approved dashboard page needs to be removed based on the Phase 2 assessment.

No new dashboard page has been added.

---

## 23. Phase Status

**Phase 1 — Project Definition: COMPLETE**

**Phase 2 — Data Acquisition and Dataset Assessment: COMPLETE**

**Next Phase: Phase 3 — Data Exploration and Cleaning**

Phase 3 will focus on profiling and cleaning the raw analytical records, including:

- duplicate detection;
- missing-value profiling;
- Pokémon identifier consistency;
- alternate Pokémon forms;
- player identifiers;
- tournament dates;
- team composition records;
- standings fields;
- match records;
- category normalization;
- source-quality flags.

No final dimensional model or SQL schema should be locked until the required exploration and cleaning work has been completed.
