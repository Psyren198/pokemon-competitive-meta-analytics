# AGENTS.md — Pokémon Competitive Meta Analytics

## 1. Purpose of This File

This `AGENTS.md` is the authoritative project reference for the **Pokémon Competitive Meta Analytics** portfolio project.

It exists to prevent scope drift, forgotten requirements, arbitrary feature additions, and inconsistent implementation decisions as the project grows across future prompts and work sessions.

All future planning, data work, SQL design, Power BI modeling, DAX, dashboard design, documentation, and portfolio presentation must follow this file unless the user explicitly approves a change.

If a future request conflicts with this file:

1. Identify the conflict clearly.
2. Do not silently alter the project.
3. Explain the proposed change and its impact.
4. Ask for explicit user approval before changing the project baseline.
5. If approved, update this file first before implementing the change.

This file is the project's **single source of truth**.

---

# 2. Project Identity

## Project Name

**Pokémon Competitive Meta Analytics**

## Portfolio Subtitle

**Analyzing competitive Pokémon usage, performance, and metagame trends using Power BI, SQL, Power Query, and DAX.**

## Project Type

End-to-end Business Intelligence and Analytics portfolio project.

## Primary Deliverable

An interactive Power BI dashboard supported by a documented analytical workflow, reproducible data preparation process, proper dimensional modeling, DAX measures, SQL transformations, and portfolio-ready documentation.

---

# 3. Portfolio Objective

The project is intended to strengthen the user's employability for entry-level and junior roles such as:

- Data Analyst
- Business Intelligence Analyst
- BI Developer
- Reporting Analyst
- Junior Data Engineer / Analytics Engineer where relevant
- Business Analyst roles with strong analytics responsibilities

The project must demonstrate practical BI skills rather than merely produce visually attractive charts.

The finished portfolio project should provide evidence of competency in:

- Requirements analysis
- Data acquisition
- Data cleaning
- SQL
- Power Query
- Data modeling
- Star schema design
- DAX
- Power BI
- Data visualization
- Analytical reasoning
- Data storytelling
- Documentation
- Git / GitHub
- Reproducibility
- Stakeholder-focused dashboard design

The project must be explainable in an interview.

---

# 4. Core Project Scenario

Assume the analyst is working for a **competitive Pokémon strategy platform**.

The platform wants to help competitive players understand the competitive metagame using data rather than relying entirely on subjective impressions.

The platform wants to understand:

- Which Pokémon dominate the current metagame.
- Which Pokémon perform well relative to their popularity.
- How the metagame changes over time.
- How tournament environments differ.
- Which Pokémon are rising or declining in usage.
- Which Pokémon consistently perform strongly.
- How types and other available characteristics are represented across competitive play.

The analyst's role is to transform raw competitive data into an interactive BI solution that supports tournament preparation and metagame analysis.

---

# 5. Primary Stakeholder

## Primary User

**Competitive Pokémon player preparing for tournaments**

The dashboard should primarily support players who want evidence-based information about the metagame before competitive events.

## Secondary Users

Secondary users may include:

- Competitive coaches
- Competitive analysts
- Pokémon strategy websites
- Tournament commentators
- Content creators
- Esports/statistics enthusiasts

Design decisions should prioritize the primary stakeholder unless explicitly approved otherwise.

---

# 6. Problem Statement

Competitive Pokémon players have access to large amounts of tournament and battle data, but identifying meaningful metagame patterns from raw statistics can be difficult.

Usage rate alone does not necessarily indicate competitive effectiveness. Comparing performance across Pokémon, tournaments, periods, formats, and regulations can require substantial manual analysis.

This project will develop an interactive Power BI analytics solution that consolidates competitive Pokémon data and enables users to analyze:

- Pokémon usage
- Competitive performance
- Tournament results
- Metagame trends
- Tournament differences
- Regulation differences

The dashboard should highlight:

- Dominant Pokémon
- Emerging threats
- Underutilized high performers
- Potentially overrepresented Pokémon
- Changes in the competitive environment over time

The project must avoid claiming that a Pokémon is objectively "better" solely from one derived metric.

---

# 7. Primary Analytical Question

The core analytical question is:

> **Which Pokémon are defining the competitive metagame, and how does their competitive performance compare with their popularity?**

All major dashboard components should support this question directly or provide useful context around it.

---

# 8. Analytical Question Framework

## 8.1 Meta Composition

The project should answer:

- Which Pokémon have the highest usage rates?
- Which Pokémon types are most represented?
- How concentrated is the metagame among the most popular Pokémon?
- How diverse or concentrated is the competitive field?

## 8.2 Performance

The project should answer:

- Which Pokémon achieve the strongest competitive results?
- Does high usage correspond with high performance?
- Which Pokémon perform disproportionately well despite relatively low usage?
- Which Pokémon are popular but do not perform proportionally as well?

## 8.3 Trends

The project should answer:

- Which Pokémon are rising in usage?
- Which Pokémon are falling in usage?
- How does usage change between regulations or time periods?
- Are particular Pokémon consistently strong across multiple tournaments?

## 8.4 Tournament Comparison

The project should answer:

- How does the metagame differ between tournaments?
- Which Pokémon achieve the most top placements?
- How does performance vary between events?
- Are certain Pokémon more successful in larger tournaments?
- How concentrated is each tournament's metagame?

---

# 9. Core KPIs

The following KPIs form the baseline project requirements.

They may only be changed if data limitations make them impossible or if the user explicitly approves a change.

## Required / Preferred KPIs

- Total Pokémon Analysed
- Total Tournaments
- Total Players and/or Teams
- Total Pokémon Appearances
- Usage Rate
- Win Rate, if supported by data
- Top Cut Appearances, if supported by data
- Top Cut Rate, if supported by data
- Average Placement, if supported by data
- Usage Change %
- Performance Rank
- Usage Rank
- Meta Share / Representation
- Tournament Count per Pokémon

Data availability must determine which measures can be implemented.

No KPI should be fabricated when the source data does not support it.

---

# 10. Derived Analytical Metric

## Performance Index

A derived **Performance Index** may be created to help identify Pokémon that perform disproportionately well or poorly relative to their popularity.

The exact formula must not be finalized until the available data is inspected.

A conceptual starting point is:

Performance Index = Performance Measure / Usage Rate

Possible performance measures could include:

- Win rate
- Top cut conversion
- Placement-based score
- Weighted tournament performance

The final metric must be:

- Clearly documented
- Reproducible
- Interpretable
- Statistically reasonable
- Explicitly described as a project-defined analytical metric

The metric must not be presented as proof that one Pokémon is objectively better than another.

---

# 11. Signature Analysis

The project's signature analytical visual is the:

## Usage vs Performance Matrix

The intended conceptual interpretation is:

| Usage | Performance | Interpretation |
|---|---|---|
| Low | High | Potentially underutilized performer |
| High | High | Meta leader |
| Low | Low | Niche / lower-performing choice |
| High | Low | Popular but potentially underperforming |

The matrix should typically use:

- X-axis: Usage Rate
- Y-axis: Performance metric
- Bubble / point: Pokémon
- Bubble size: Optional sample-size-related measure such as appearances

The labels used in the final dashboard must be carefully phrased so they do not overstate causality or competitive quality.

---

# 12. Dashboard Scope

The project baseline consists of approximately **five core pages plus one recommended analytical findings page**.

Do not add or remove dashboard pages without explicit approval.

---

# 13. Dashboard Page Specifications

## Page 1 — Meta Overview

### Purpose

Provide an executive-level overview of the current competitive environment.

### Intended Questions

- What does the current metagame look like?
- Which Pokémon dominate usage?
- What are the most represented types?
- How concentrated is the meta?

### Potential Components

- KPI cards
- Top Pokémon by usage
- Type distribution
- Meta share
- Top Pokémon table
- Usage ranking
- Summary trend indicator
- Filters / slicers relevant to the page

---

## Page 2 — Meta Trends

### Purpose

Show how the metagame changes over time.

### Intended Questions

- Which Pokémon are rising?
- Which Pokémon are falling?
- How does usage change by period?
- How do regulations differ?

### Potential Components

- Usage over time
- Rank movement
- Biggest risers
- Biggest fallers
- Regulation comparison
- Tournament-to-tournament change
- Time-based slicers

---

## Page 3 — Pokémon Performance

### Purpose

Compare popularity with competitive results.

### Intended Questions

- Which Pokémon perform strongly?
- Does popularity correlate with performance?
- Which Pokémon overperform or underperform relative to usage?

### Required Signature Component

**Usage vs Performance Matrix**

### Additional Potential Components

- Win rate
- Top cut rate
- Average placement
- Usage vs performance comparison
- Performance ranking
- Conditional formatting

---

## Page 4 — Pokémon Deep Dive

### Purpose

Allow users to inspect one Pokémon in detail.

### Intended Power BI Feature

Preferably use **drill-through** or an equivalent focused selection experience.

### Potential Components

For the selected Pokémon:

- Usage Rate
- Win Rate
- Top Cut Rate
- Average Placement
- Usage Change
- Tournament appearances
- Tournament performance
- Usage trend
- Type information
- Common partners, if supported by the available data
- Item / ability / move / Tera Type data only if available and later approved within scope

---

## Page 5 — Tournament Analysis

### Purpose

Compare competitive environments across events.

### Intended Questions

- How does the meta differ between tournaments?
- Which Pokémon dominate particular events?
- Are certain environments more concentrated?
- How does tournament size affect observed results?

### Potential Components

- Tournament comparison
- Top Pokémon per tournament
- Type mix
- Meta concentration
- Top performers
- Event size
- Event date
- Relevant geographic or regulation filters if available

---

## Page 6 — Analytical Findings

### Status

Recommended and currently part of the project baseline.

### Purpose

Demonstrate data storytelling rather than stopping at visualization.

### Content

The page should summarize evidence-based findings such as:

- Metagame concentration
- Significant usage shifts
- Underutilized high performers
- Popular but lower-converting Pokémon
- Tournament differences
- Regulation differences

All findings must be based on actual calculated results from the dataset.

No findings should be written in advance of analysis.

---

# 14. Filters and Slicers

The model should be designed to support the following where data allows:

- Tournament
- Date
- Period
- Regulation
- Competitive Format
- Pokémon
- Primary Type
- Secondary Type
- Generation
- Tournament Size

Possible future slicers, only if supported by data and useful:

- Country
- Region
- Item
- Ability
- Tera Type
- Move

These optional fields must not be treated as guaranteed requirements before Phase 2 data assessment.

---

# 15. Scope — In Scope

The following are currently within project scope:

- Competitive Pokémon data
- Pokémon usage
- Tournament participation
- Tournament results
- Pokémon attributes
- Time trends
- Regulation comparisons
- Tournament comparisons
- Performance analysis
- Type analysis
- Data cleaning
- SQL transformations
- Power Query ETL
- Dimensional modeling
- DAX
- Power BI visualization
- Analytical findings
- GitHub documentation

---

# 16. Scope — Out of Scope

The following are excluded from Version 1 unless explicitly approved later:

- Tournament winner prediction
- Machine learning
- Automated team recommendation
- Team-generation algorithms
- Damage calculation engines
- Full moveset optimization
- Player Elo systems
- Player ranking systems
- Pokémon Trading Card Game analytics
- Casual battle analytics
- Main-story gameplay analytics
- Game sales analytics
- Pokémon GO analytics
- Web application development
- Mobile application development
- Real-time dashboard streaming
- Automated AI recommendations

Do not introduce these features casually.

---

# 17. Time-Period Rule

The project should focus on a **recent competitive era** rather than attempting to analyze the entire history of competitive Pokémon.

The exact final period will be chosen during Phase 2 after reviewing available datasets.

Initial preference:

- Recent 2025–2026 competitive data
- Current or recent regulations
- Enough historical coverage to support meaningful trend analysis

The guiding rule is:

> **Data availability determines the final time scope.**

Do not force a time period that results in incomplete or misleading analysis.

---

# 18. Data Granularity Rule

The final data grain must be explicitly documented.

The preferred possibilities are:

### Option A — Tournament-Pokémon Level

One row per:

**Tournament × Pokémon**

Example measures:

- Usage count
- Usage rate
- Wins
- Losses
- Top cut appearances
- Average placement

### Option B — Team-Level

One row or normalized set of rows representing Pokémon selections by one competitive team.

### Option C — Battle-Level

One row per competitive battle or normalized battle participant record.

Battle-level data is preferred only if it is reliable, manageable, and sufficiently complete.

The project must never combine grains carelessly.

Fact tables must have clearly defined grain before implementation.

---

# 19. Target Data Architecture

The project should use a proper dimensional model rather than a single flat reporting table.

The baseline concept is:

```text
                 DimDate
                    |
                    |
DimPokemon ---- FactPokemonPerformance ---- DimTournament
                    |
                    |
              DimRegulation
                    |
                    |
                 DimFormat
```

The exact model may evolve after Phase 2 data assessment.

Any change must preserve dimensional-modeling principles.

---

# 20. Expected Dimension Tables

Potential dimensions include:

## DimPokemon

Possible fields:

- PokemonID
- PokemonName
- Type1
- Type2
- Generation
- Category
- BaseHP
- BaseAttack
- BaseDefense
- BaseSpAttack
- BaseSpDefense
- BaseSpeed

Only use attributes supported by reliable source data.

## DimTournament

Possible fields:

- TournamentID
- TournamentName
- TournamentDate
- Location
- Country
- PlayerCount
- RegulationID
- FormatID

## DimDate

Typical calendar fields:

- Date
- Year
- Quarter
- Month
- Month Number
- Week
- Year-Month

## DimRegulation

Possible fields:

- RegulationID
- RegulationName
- StartDate
- EndDate

## DimFormat

Possible fields:

- FormatID
- FormatName
- Ruleset / category where appropriate

Additional dimensions may be added only when supported by the source data and analytical requirements.

---

# 21. Expected Fact Table

A possible baseline fact table is:

## FactPokemonPerformance

Potential fields:

- TournamentID
- PokemonID
- DateKey
- RegulationID
- FormatID
- UsageCount
- UsageRate
- Wins
- Losses
- WinRate
- TopCutCount
- TopCutRate
- Points
- AveragePlacement

This structure is provisional until Phase 2 confirms the available source data and final grain.

---

# 22. Technology Stack

The baseline technology stack is:

## Required

- **Power BI Desktop**
- **Power Query**
- **DAX**
- **SQL**
- **Git**
- **GitHub**

## SQL Platform

The exact SQL platform may be selected later based on practicality.

Potential options include:

- PostgreSQL
- SQL Server
- SQLite for local analytical use

The selection should support portfolio value, reproducibility, and reasonable setup complexity.

Do not add unnecessary infrastructure purely to make the project appear more complex.

---

# 23. Intended Data Pipeline

The target high-level workflow is:

```text
Source Data
    |
    v
Raw Data Storage
    |
    v
SQL Database / Staging
    |
    v
SQL Cleaning / Transformation
    |
    v
Analytical Tables / Views
    |
    v
Power Query
    |
    v
Power BI Data Model
    |
    v
DAX Measures
    |
    v
Dashboard
    |
    v
Analytical Findings
    |
    v
GitHub Portfolio Documentation
```

The exact sequence may be adapted if the data source makes a different ingestion approach more sensible.

---

# 24. SQL Requirements

SQL should be used meaningfully.

The project should demonstrate some combination of:

- SELECT
- WHERE
- JOIN
- GROUP BY
- CASE
- CTEs
- Window functions where appropriate
- Aggregation
- Data cleaning
- Views
- Deduplication
- Standardization
- Data-quality checks

SQL should not be included merely as decoration.

If a transformation is performed in SQL, it should have a clear analytical or modeling reason.

---

# 25. Power Query Requirements

Power Query should be used for reproducible ETL and preparation within Power BI.

Possible responsibilities include:

- Data type enforcement
- Column renaming
- Removing unnecessary columns
- Standardizing Pokémon names
- Handling alternate forms
- Handling nulls
- Joining lookup tables
- Filtering invalid records
- Creating staging queries
- Loading final model tables

Manual edits in Excel should be minimized.

The workflow should remain reproducible from raw data.

---

# 26. DAX Requirements

The project should demonstrate more than basic aggregation.

Potential required measures include:

- Total Appearances
- Total Tournaments
- Total Players / Teams
- Usage Rate
- Win Rate
- Top Cut Rate
- Average Placement
- Previous Period Usage
- Usage Change
- Usage Change %
- Rank by Usage
- Rank by Performance
- Meta Share
- Performance Index

Additional DAX may include:

- Running totals
- Dynamic ranking
- Context-aware measures
- Selected Pokémon metrics
- Selected tournament comparisons
- Period-over-period change

Measures must be documented and understandable.

Avoid unnecessarily complex DAX when a simpler solution is correct.

---

# 27. Visualization Principles

The dashboard must prioritize analytical clarity over decoration.

Use visuals because they answer a question, not because they look impressive.

Preferred principles:

- Clear hierarchy
- Consistent formatting
- Limited clutter
- Appropriate chart selection
- Accessible labels
- Meaningful tooltips
- Useful conditional formatting
- Consistent number formatting
- Thoughtful slicer placement
- Logical page flow
- Minimal unnecessary icons or decorative elements

Avoid:

- Excessive gauges
- 3D charts
- Decorative charts that obscure comparisons
- Too many colors
- Pokémon-themed styling that compromises professionalism
- Visual clutter
- Redundant KPI cards
- Charts with no analytical purpose

The final result may retain a subtle Pokémon-inspired identity, but it should still look professional enough for a job portfolio.

---

# 28. Data Integrity Rules

All project analysis must be based on traceable source data.

The project must:

- Record dataset sources
- Record download dates
- Preserve raw data where legally and technically reasonable
- Document transformations
- Document assumptions
- Identify missing data
- Identify exclusions
- Avoid fabricated values
- Avoid unsupported metrics
- Avoid mixing incompatible tournament formats without documentation
- Avoid misleading comparisons across different regulations

Any known data-quality limitation should be documented.

---

# 29. Interpretation Rules

The project must distinguish between:

- Popularity
- Usage
- Win rate
- Tournament conversion
- Placement
- Overall competitive strength

These are not interchangeable.

For example:

- High usage does not automatically mean high performance.
- High win rate from a small sample may not imply broad strength.
- Strong top-cut conversion may be influenced by player quality.
- Tournament placement is affected by more than Pokémon choice.

Dashboard wording should avoid implying causality when only association is observed.

---

# 30. Change-Control Rules

This section is mandatory.

Future work must not silently change the project.

## Any Proposed Change Must Be Classified As:

### A. Clarification

Does not change scope.

Example:

- Renaming a chart title
- Rewording a KPI description

No major approval process is required.

### B. Implementation Detail

Changes how an approved feature is built without changing project intent.

Example:

- Choosing PostgreSQL instead of SQL Server

The rationale should still be documented.

### C. Scope Change

Adds, removes, or materially changes an agreed feature.

Examples:

- Adding machine learning
- Removing tournament analysis
- Replacing Power BI with Tableau
- Adding player ranking
- Removing SQL
- Adding automated team recommendation
- Changing the project from competitive Pokémon to general Pokémon analytics

These changes require explicit user approval before implementation.

---

# 31. Rule Against Feature Creep

Do not add features merely because:

- They are technically possible.
- They appear impressive.
- Another dashboard includes them.
- A new dataset contains extra columns.
- A future prompt casually mentions them without clearly requesting a scope change.

Before adding a new feature, check whether it:

1. Supports the primary analytical question.
2. Helps the primary stakeholder.
3. Strengthens the intended portfolio skills.
4. Fits Version 1 scope.
5. Can be supported by reliable data.

If not, treat it as a future enhancement.

---

# 32. Rule Against Feature Removal

Do not remove agreed features simply because implementation becomes difficult.

Instead:

1. Identify the difficulty.
2. Investigate alternatives.
3. Explain any data or technical limitation.
4. Propose a substitute if appropriate.
5. Obtain user approval before removing the feature.

---

# 33. Phase Plan

The project should follow the planned phases below.

## Phase 1 — Project Definition

Status: **Completed**

Includes:

- Project identity
- Scenario
- Stakeholder
- Problem statement
- Analytical questions
- KPI definitions
- Dashboard page plan
- Initial scope
- Portfolio objectives

## Phase 2 — Data Acquisition and Dataset Assessment

Tasks:

- Identify candidate data sources
- Evaluate reliability
- Evaluate licensing / usage conditions
- Inspect available columns
- Determine time coverage
- Determine data grain
- Assess missing data
- Select primary and secondary datasets
- Decide final analytical scope based on data availability

No final schema should be locked before this assessment.

## Phase 3 — Data Exploration and Cleaning

Tasks:

- Profile raw datasets
- Identify duplicates
- Identify missing values
- Standardize names
- Handle Pokémon forms
- Validate IDs
- Validate dates
- Normalize categories
- Document quality issues

## Phase 4 — Data Modeling

Tasks:

- Define final fact grain
- Create dimensions
- Create fact tables
- Create relationships
- Validate star schema
- Create data dictionary

## Phase 5 — SQL Transformation Layer

Tasks:

- Load data
- Create staging logic
- Clean data
- Create transformations
- Build analytical views
- Validate outputs

## Phase 6 — Power BI Connection and Power Query

Tasks:

- Connect to prepared data
- Perform final ETL
- Create model tables
- Configure relationships
- Hide technical fields where appropriate

## Phase 7 — DAX Development

Tasks:

- Create base measures
- Create derived measures
- Create ranking
- Create time analysis
- Create usage change
- Create performance metrics
- Validate all measures

## Phase 8 — Dashboard Design

Tasks:

- Build pages 1–6
- Implement slicers
- Implement drill-through
- Implement tooltips
- Implement formatting
- Optimize layout
- Validate interactions

## Phase 9 — Analytical Findings

Tasks:

- Examine results
- Identify meaningful patterns
- Validate findings
- Write evidence-based insights
- Avoid unsupported causal conclusions

## Phase 10 — GitHub Documentation

Tasks:

- Write README
- Document architecture
- Document data sources
- Document model
- Document KPIs
- Include dashboard screenshots
- Include limitations
- Include project lessons
- Include reproducibility instructions

## Phase 11 — Portfolio / LinkedIn Presentation

Tasks:

- Prepare concise project summary
- Select screenshots
- Explain business problem
- Explain analytical approach
- Highlight technical skills
- Present major findings
- Link repository or dashboard where appropriate

---

# 34. Phase-Gate Rule

Do not skip phases casually.

Before moving to the next major phase:

- Confirm the previous phase has enough information to support it.
- Record important decisions.
- Update this file if the baseline changes.
- Avoid building visuals before the dataset and model are sufficiently understood.

---

# 35. Version 1 Success Criteria

Version 1 is successful if the user can confidently explain:

## Why was the project created?

To investigate the relationship between Pokémon popularity and competitive performance.

## Who is the dashboard for?

Competitive Pokémon players and analysts preparing for tournaments.

## How was the data structured?

Using a documented dimensional / star-schema model.

## Why was SQL used?

To clean, transform, combine, validate, and structure source data for analysis.

## Why was Power Query used?

To create reproducible ETL transformations and prepare model-ready tables.

## What was calculated with DAX?

Usage, performance, trends, rankings, period changes, and comparative metrics.

## What did the analysis discover?

Concrete, evidence-based findings supported by the final dataset.

---

# 36. Portfolio Quality Standard

The project should be judged by whether it demonstrates:

- Analytical thinking
- Technical competency
- Good data modeling
- Reproducibility
- Communication
- Clear business framing
- Professional presentation
- Appropriate limitations
- Evidence-based findings

The dashboard should not be considered complete simply because all pages contain visuals.

---

# 37. Documentation Standard

Important decisions should be documented throughout the project.

At minimum, preserve:

- Data source names
- Data source URLs
- Download dates
- Dataset versions if available
- Table grain
- Transformation decisions
- KPI formulas
- DAX formulas
- SQL scripts
- Data-quality issues
- Assumptions
- Exclusions
- Dashboard screenshots
- Final findings
- Limitations

---

# 38. Repository Guidance

The eventual GitHub repository should be organized clearly.

A possible structure is:

```text
pokemon-competitive-meta-analytics/
|
|-- AGENTS.md
|-- README.md
|
|-- data/
|   |-- raw/
|   |-- processed/
|
|-- sql/
|   |-- schema/
|   |-- staging/
|   |-- transformations/
|   |-- views/
|
|-- powerbi/
|   |-- pokemon_meta_analytics.pbix
|
|-- docs/
|   |-- data_dictionary.md
|   |-- methodology.md
|   |-- dashboard_guide.md
|   |-- limitations.md
|
|-- images/
|   |-- dashboard/
|
`-- notes/
    `-- project_decisions.md
```

This structure is provisional and may be adjusted as implementation needs become clearer.

---

# 39. Data Source Selection Principles

During Phase 2, candidate sources should be evaluated based on:

- Reliability
- Completeness
- Time coverage
- Tournament coverage
- Data granularity
- Accessibility
- Reproducibility
- Licensing / terms of use
- Ease of ingestion
- Stability
- Ability to support the core analytical questions

Preference should be given to sources that provide structured data such as:

- CSV
- JSON
- API
- Consistently structured downloadable datasets

Manual scraping should not be the default approach when cleaner alternatives exist.

---

# 40. Professional Framing Rule

Although the topic is Pokémon, the project must be presented professionally.

The portfolio narrative should emphasize:

- Competitive analytics
- Metagame analysis
- Decision support
- Data modeling
- Performance comparison
- Trend analysis
- BI engineering workflow

Avoid framing the project as merely:

- A fan project
- A Pokédex
- A collection of Pokémon facts
- A decorative game-themed dashboard

The gaming theme is the domain.

The project itself is a serious analytics case study.

---

# 41. Interview Readiness Rule

Every technical element added to the project should be something the user can reasonably explain during an interview.

Do not implement unnecessary complexity that the user cannot defend.

For every important design decision, the user should eventually understand:

- What was done
- Why it was done
- What alternative existed
- Why the chosen approach was appropriate
- What limitations remain

---

# 42. Future Enhancements

The following may be considered after Version 1 is complete, but are not part of the baseline:

- Automated data refresh
- Expanded historical regulation coverage
- Player-level analysis
- Team composition analysis
- Pokémon pairing / synergy networks
- Move analysis
- Ability analysis
- Item analysis
- Tera Type analysis
- Additional competitive formats
- Python statistical analysis
- Predictive modeling
- Public web deployment / embedded reporting
- Microsoft Fabric integration

These must remain future enhancements unless the user explicitly promotes them into Version 1 scope.

---

# 43. Current Project Baseline Summary

| Item | Baseline Decision |
|---|---|
| Project | Pokémon Competitive Meta Analytics |
| Domain | Competitive Pokémon |
| Primary Tool | Power BI |
| Supporting Tools | SQL, Power Query, DAX, Git, GitHub |
| Primary Stakeholder | Competitive Pokémon player |
| Primary Question | Which Pokémon define the meta, and how does performance compare with popularity? |
| Core Analysis | Usage, performance, trends, tournament comparison |
| Signature Analysis | Usage vs Performance Matrix |
| Dashboard Pages | Approximately 6 |
| Data Model | Star schema / dimensional model |
| Time Scope | Recent competitive era, finalized in Phase 2 |
| SQL | Required and meaningful |
| Power Query | Required |
| DAX | Required |
| Data Storytelling | Required |
| GitHub Documentation | Required |
| Version 1 ML | Out of scope |
| Team Recommendation System | Out of scope |
| Portfolio Goal | Demonstrate end-to-end BI competency |

---

# 44. Instruction to Future Agents / Assistant Sessions

Before making a material project decision:

1. Read this `AGENTS.md`.
2. Identify the current project phase.
3. Check whether the requested work is in scope.
4. Preserve all previously approved requirements.
5. Do not invent new requirements.
6. Do not remove existing requirements without approval.
7. Base analytical features on available data.
8. Prefer reproducible workflows.
9. Keep the project professionally framed.
10. Optimize decisions for portfolio value and interview readiness.
11. Clearly distinguish facts from assumptions.
12. Document material changes.
13. Update this file whenever the approved baseline changes.

If there is uncertainty, default to the existing baseline rather than introducing a new direction.

---

# 45. Current Status

**Phase 1 — Project Definition: COMPLETE**

**Phase 2 — Data Acquisition and Dataset Assessment: COMPLETE**

## Phase 2 Locked Decisions

- Primary analytical source: VGC History.
- Analytical population: 2026 Championship Series, Masters division.
- Selected population: 36 tournaments.
- Event tiers: 26 Regionals, 6 Special Events, 3 Internationals, 1 Worlds.
- Regulations: H, F, I, M-A, M-B.
- Games: Scarlet & Violet and Pokémon Champions.
- All 36 verified tournaments remain in the overall analytical population.
- No global completeness threshold will automatically exclude tournaments.
- Analytical eligibility will be KPI-specific.
- Pokémon usage will use known team sheets as the denominator.
- Tournament attendance, standings coverage, team-sheet coverage, and match coverage are distinct populations.
- Source discrepancies will be preserved and flagged rather than manually corrected.
- Buenos Aires Special Event 2026 has Swiss-only standings and requires special handling for final-placement and top-cut metrics.
- Ladder statistics will not be silently mixed with official tournament statistics.
- Final dimensional schema remains unlocked until Phase 4.
- Performance Index formula remains unlocked until supported by later analysis.

**Next Planned Phase: Phase 3 — Data Exploration and Cleaning**

Phase 3 will profile the raw analytical records for duplicates, missing values, Pokémon identifiers and forms, player identifiers, dates, team composition, standings, matches, category consistency, and source-quality issues.

No final SQL schema or dimensional model is considered locked until the required exploration and cleaning work has been completed.

