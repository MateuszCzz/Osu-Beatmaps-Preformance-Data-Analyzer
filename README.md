# Osu-Beatmaps-Preformance-Data-Analyzer
A Google Colab data pipeline that mass-collects player score data from the osu! API, processes tens of thousands of records, and surfaces maps which are statistically most rewarding for a specific rank bracket. This information is valuable - but doesn't exist anywhere officially. This pipeline builds it from scratch by scraping raw behavioral data at scale from multiple surces.

### Data Collection

The system has potential to pull from three sources to maximize player coverage within the target rank window:

- **Leaderboard crawl** — walks country-by-country through all country codes, paginating the official ranking API until the rank ceiling is hit
- **Community dataset** — ingests a external CSV snapshot of hundreds of thousands of historical player records
- **Sequential ID scan** — brute-forces the full user ID space in batches of 50, catching players missed by rankings

### Profitability Analysis

Once collected, scores are grouped by **map + mod combination** and each group is scored across several value indicators:

- **Appearance rate** — how often the map shows up in top plays across the player pool (the core demand signal)
- **Average PP yield** — mean performance points earned, indicating raw point value
- **Missless rate** — share of plays with zero misses, signaling how consistently achievable a full combo is
- **HD usage rate** — how many players apply Hidden mod, which boosts PP by ~6% at low cost
- **Average accuracy** — reveals whether the map rewards precision or is cleared comfortably

### Data Enrichment

A fully formatted Excel workbook with 26 columns per beatmap, sorted based on appearence rate as well as direct hyperlinks to each map — ready to sort, pivot, and analyze to identify the best targets for ambitious players.

Explore a sample output dataset covering the 300,000–60,000 range, filtered for scores above 200 points: [view](https://docs.google.com/spreadsheets/d/1lteMcQXg7Wzc6BufERoOIoXF7Nc4rNirhqP6k43EEqQ)
