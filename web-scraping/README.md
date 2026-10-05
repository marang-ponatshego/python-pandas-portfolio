# Web Scraping with BeautifulSoup & Pandas

## Overview

A web scraping project that extracts structured data from a live
Wikipedia page and converts it into a clean, analyzable pandas
DataFrame. The target is the *List of largest companies in the United
States by revenue* — a ranked table of the top private US companies.

**Tools:** Python — `requests`, `BeautifulSoup`, `pandas`
**File:** `web_scraping.ipynb`
**Output:** `companies.csv` (not committed — see Notes)

---

## Source

**URL:**
`https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue`

The page contains a ranked table of the largest private US companies,
including rank, revenue, employee count, industry, and headquarters.

---

## What the notebook does

### 1. Fetch the page
- Uses `requests.get()` with a custom `User-Agent` header
  (Wikipedia blocks requests that don't identify themselves)
- Confirms the response returned successfully

### 2. Parse with BeautifulSoup
- Converts the raw HTML into a parseable `BeautifulSoup` object
- Locates the target `<table>` element by position

### 3. Extract column headers
- Iterates through the header row (`<th>` tags)
- Builds the column list dynamically rather than hardcoding it

### 4. Extract row data
- Iterates through each data row (`<tr>` tag)
- For each row, extracts all cells (`<td>` tags)
- Strips whitespace from each cell
- Appends each row to the DataFrame using `df.loc[len(df)]`

### 5. Export
- Saves the final DataFrame to `companies.csv` with `index=False`

---

## Sample output

| Rank | Name | Industry | Revenue (USD billions) | Employees | Headquarters |
|---|---|---|---|---|---|
| 1 | Cargill | Food & Drink | 154 | 155,000 | Minnetonka, Minnesota |
| 2 | Koch | Multicompany | 125 | 120,000 | Wichita, Kansas |
| 3 | Publix Super Markets | Food Markets | 59.7 | 260,000 | Lakeland, Florida |
| 4 | Mars | Food & Drink | 55 | 150,000 | McLean, Virginia |
| 5 | H-E-B Grocery Company | Food Markets | 49.57 | 175,000 | San Antonio, Texas |

---

## What the data shows

From the top 10 entries alone, some patterns are worth noting:

- **Food is the dominant sector** — Cargill, Publix, Mars, and H-E-B
  all sit in the top 5, reflecting the sheer scale of US food
  distribution and grocery.
- **Revenue is heavily top-weighted** — Cargill's $154B is roughly
  **6.5× larger** than the 10th company's revenue ($23.5B).
- **Employee count doesn't track revenue** — Publix Super Markets has
  the highest headcount in the top 5 (260,000) while ranking third in
  revenue, showing that different industries use very different
  revenue-per-employee ratios.

---

## Files in this folder

| File | What it is |
|---|---|
| `web_scraping.ipynb` | The scraping notebook — fetch, parse, build DataFrame |

---

## Notes

- The notebook is **live-scraping** — it fetches the current version
  of the Wikipedia page every time it runs. The output may differ from
  the snapshot shown in the notebook if Wikipedia has updated the page.
- The output `companies.csv` is written to a local path in the
  notebook. Update the file path to your own location before running.
- Website scraping should always respect the site's `robots.txt` and
  terms of service. Wikipedia permits this kind of use.

---

## Skills demonstrated

- HTTP requests with `requests` (including `User-Agent` header handling)
- HTML parsing with BeautifulSoup: `find`, `find_all`, nested element traversal
- Working with nested HTML tables
- Building a DataFrame row-by-row with `df.loc[]`
- String cleaning with `.strip()` inside list comprehensions
- Exporting clean data to CSV with `to_csv()`
