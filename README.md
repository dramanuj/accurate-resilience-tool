# SCREENING TOOL FOR FACTORY-LEVEL RESILIENCE INDICATORS
A resilience indicator screening tool developed as part of the EU-funded ACCURATE project. This interactive, browser-based tool lets you browse, filter, and sort resilience indicators extracted from the academic literature. Each indicator is linked to its source publication, resilience principle(s), indicator type, disruption stage, and disruption level.


## Access:
This tool is hosted here: https://dramanuj.github.io/accurate-resilience-tool/index.html


## Layout & Usage
The tool is organised into two main areas:
- Filter panel (top) — a search bar and four rows of clickable chip filters.
- Results table (bottom) — a scrollable, sortable table showing the indicators that match your current filters.  
A live counter between the two areas always tells you how many indicators are currently displayed out of the total dataset (e.g. "34 indicators shown (of 93)").
All filters are additive across categories (an indicator must satisfy every active filter group) and inclusive within a category (selecting multiple chips in the same row returns indicators matching any of them).

### Text search
The search bar at the top left performs a free-text search across indicator names, descriptions, author names, publication titles, and citation keys. Results update as you type.

### Resilience principle
The tool lists every resilience principle present in the dataset (e.g. Redundancy, Robustness, Flexibility, Recoverability, Resourcefulness, etc.). Click one or more buttons to restrict the table to indicators tagged with those principles.
- Hide N/A checkbox — When ticked, indicators that have no assigned principle (N/A) are removed from the results. Useful when you only want principle-mapped indicators.

### Indicator type
Three types: Topological, Attributional, and Performance.
- Exact match only checkbox: By default, the filter uses partial/substring matching so that combined types (e.g. "Topological/Performance") appear when either constituent type is selected. Ticking the Exact match only checkbox restricts results to indicators whose type string matches the selected button exactly.

### Resilience stage
Four buttons represent the temporal phases of a disruption: Pre-Disruption, System Decline, Recovery, and Post-Disruption. Select one or more to focus on a specific phase.

### Disruption level
Six buttons representing the scale at which the indicator has been validated: Machine, Operation, Enterprise, Market, Society, and No Validation Case. The last option captures indicators that were proposed theoretically without an empirical validation case.

### Active filter tags
Whenever a filter is active, a coloured tag appears below the buttons summarising your current selection (e.g. Principle: Redundancy, Stage: Recovery, Exact type match). Click the × on any tag to remove that individual filter without clearing everything else.

### Clearing all filters
Click the Clear all filters button (top right, next to the search bar) to reset every filter, checkbox, and search term back to the default state and display the full dataset.

### Sorting the table
Click any column header in the results table to sort by that column. Clicking the same header again toggles between ascending (▲) and descending (▼) order. 

### Reading the results table
Each row represents one indicator and contains six columns:
- Indicator: The indicator name in bold, followed by a short description in grey text.
- Principles: One or more coloured pills showing the resilience principle(s) the indicator maps to.
- Indicator Type: Topological, Attributional, Performance, or a combination.
- Stage: The disruption stage the indicator is designed for.
- Disruption Level: Amber-tinted pills showing the scale(s) at which the indicator was validated.
- Publication: The source paper's title, first author, year, and journal. Where available, an "Open paper" link takes you directly to the DOI or URL of the original publication.


### Example workflows
- "Which performance indicators exist for the recovery phase?" → Click the Performance button under Indicator Type, then click Recovery under Resilience Stage.
- "Show me all indicators related to Redundancy or Flexibility, excluding unvalidated ones" → Click Redundancy and Flexibility under Resilience Principle. Avoid selecting No Validation Case under Disruption Level, and leave that filter group empty — all disruption levels will then be shown, including validated ones.
- "Find indicators from a specific author" → Type the author's surname into the search bar.
- "I only want strictly Topological indicators, not mixed types like Topological/Performance" → Click Topological under Indicator Type and tick the Exact match only checkbox.


# Submitting a New Resilience Indicator

The Resilience Indicators Explorer draws on a structured database, and every entry follows the same fields and controlled vocabularies so that filtering, sorting, and searching work consistently across the tool. If you would like to propose a new indicator for inclusion, please  prepare the indicator using the fields and allowed values below and email it to the authors.

Please structure each new indicator as a single JSON object using the fields and controlled terms below, and send it to me by email. Do not edit the tool directly.

## Fields and controlled terms

- **`indicator`** (text) – A short, descriptive name for the indicator.
- **`description`** (text) – One or two sentences explaining what the indicator measures.
- **`indicator_type`** (choose one) – `Topological`, `Attributional`, `Performance`.
- **`method`** (text) – A brief description of how the indicator is measured or calculated (e.g. "Survey of floor layout").
- **`stage`** (choose one) – `Pre-Disruption`, `System Decline`, `Recovery`, `Post-Disruption`.
- **`principles`** (list — choose one or more) – `Flexibility`, `Growth`, `Modularity`, `Reconfigurability`, `Recoverability`, `Redundancy`, `Reliability`, `Resourcefullness`, `Robustness`, `Safety`, `Financial Loss`. If none apply, use `["N/A"]`.
- **`disruption_levels`** (list — choose one or more) – `Machine`, `Operation`, `Enterprise`, `Market`, `Society`. If the indicator has not been tested against a specific disruption case, use `["No Validation Case"]`.
- **`cite_key`** (text) – A short citation key for the source, typically `authorYYYY` (e.g. `smith2023`).
- **`title`** (text) – Title of the source publication.
- **`author`** (text) – Author names, joined with " and " (e.g. `Smith, John and Lee, Kim`).
- **`year`** (text) – Publication year.
- **`journal`** (text) – Journal or venue name.
- **`doi`** (text) – DOI of the publication, if available.
- **`url`** (text) – A direct link to the publication (used if no DOI is available).

Please keep entries within these existing controlled terms rather than introducing new ones, so the indicator fits into the current filtering structure. If you feel a new term or category is genuinely needed, flag this separately in your email so it can be considered before being added.

## Example submission

```json
{
  "indicator": "Recovery Time Ratio",
  "description": "The ratio of actual recovery time to the target recovery time defined for a process following a disruption.",
  "indicator_type": "Performance",
  "method": "Calculated from operational logs comparing planned versus actual recovery duration.",
  "stage": "Recovery",
  "principles": ["Recoverability", "Robustness"],
  "cite_key": "smith2023",
  "title": "Measuring Recovery Performance in Manufacturing Systems",
  "author": "Smith, John and Lee, Kim",
  "year": "2023",
  "journal": "Journal of Manufacturing Systems",
  "doi": "10.1016/j.jmsy.2023.01.001",
  "url": "https://doi.org/10.1016/j.jmsy.2023.01.001",
  "disruption_levels": ["Operation", "Enterprise"]
}
```



## Citation
Bushagour A., Hassan H., Martiny T., Mansour R., Boudjadar J., Layton A., & Ramanujan D. (2025) "A Systematic Review of Indicators for Assessing Manufacturing Resilience at the Factory Level". Anonymous Journal (in review)


## Contact
For any questions or feedback on this tool, contact one of the following authors: devr [AT] dtu [DOT] dk; amira [DOT] bushagour [AT] mpe [DOT] au [DOT] dk
   
## Disclaimer
Artificial Intelligence (AI) based tools were used to assist with the programming of this screening tool. No AI tools were used in the literature review process itself, including the formulation of the search terms, article screening, analysis, or categorisation of sources.

## Acknowledgements
Funded by the European Union. This project has received funding from the European Union’s Horizon Europe research and innovation programme under the Grant Agreement n° 101138269. Views and opinions expressed are, however, those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Executive Agency (REA). Neither the European Union nor the granting authority can be held responsible for them.
