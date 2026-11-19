# College-town home sales

## Start here (delete this section before you submit)

This repository is your starting point for the Home Sales case. It already holds the dataset, its description sheet, project instructions for your AI coding agent, and outlines of the README and agent log that the case asks for.

1. **Turn on GitHub Pages.** In this repository, open **Settings**, then **Pages**. Under "Build and deployment," set **Source** to **GitHub Actions**. GitHub may suggest workflows to add. Skip them: this repository already has one, `.github/workflows/pages.yml`.
2. **Publish for the first time.** Open the **Actions** tab, choose **Publish site to GitHub Pages** in the sidebar, click **Run workflow**, then click **Run workflow** again to confirm. If the tab already shows a failed run from when you created the repository, that's expected: Pages wasn't turned on yet. When the new run shows a green check, your site is at `https://your-username.github.io/your-repo-name/`. It shows a placeholder page until you replace `index.html`.

    From then on, every push to the main branch publishes the site within a few minutes. If the live site doesn't show a change, open the **Actions** tab. A red X means the publish failed, and the run's log says why.
3. **Open the repository in your AI coding agent.** Its project instructions are in `AGENTS.md`. If your agent reads its instructions from a file with a different name, check its documentation and copy `AGENTS.md` to that name. Add to the instructions as you learn what your agent needs.
4. **Read `docs/data_description_sheet.md`** before you ask the agent for any analysis.
5. **Build in small steps,** as the setup guide describes. Add an entry to `AGENT_LOG.md` each time you work with the agent.
6. **Fill in every section below** before you submit.

| Path | What it is |
|---|---|
| `index.html` | The site: a dashboard of median sale price by city. |
| `data/college_town_home_sales.csv` | The dataset, version 1.0: 35,442 rows. Your site reads this file. |
| `data/college_town_home_sales.xlsx`, `.sqlite`, `.duckdb`, `.parquet` | The same data in Excel, SQLite, DuckDB and Parquet formats, with identical values |
| `docs/data_description_sheet.md` | What every column means, and five problems in the data |
| `AGENTS.md` | Project instructions for your AI coding agent |
| `AGENT_LOG.md` | Your agent log |
| `scripts/` | Scripts that make smaller data files for the site |
| `.github/workflows/pages.yml` | Publishes the site to GitHub Pages each time you push to main. It publishes your files as they are. If you switch to a framework that needs a build step, have your agent update it. |

Don't edit any of the five dataset files. Your site needs only the CSV file. The other formats make it easier to check numbers a second way, for example with a pivot table in Excel or a SQL query on the SQLite file. In SQLite and DuckDB, the table is named `home_sales`.

## What this site is for

This site is for students looking for housing near different college campuses. It answers one question: what is the median sale price of homes sold in each college town? It shows a bar chart, a sortable table and the key figures, with the calculation rule stated on the page. It is a findings site only. It does not take contact details or other input.

## Live site

https://bianca-ranchhod.github.io/campustown-home-sales-site/

This address follows GitHub Pages' pattern for this repository. It goes live once the pull request is merged into `main`, and I have not checked that it loads.

## Data notes

- **How each figure is defined.** The median sale price for a city is the middle sale price of that city's sales, after sales under $10,000 are left out. The sales count is the number of sales used for that city. The lowest and highest city medians are the smallest and largest of those city medians. The total sales count is the sum of the city counts.
- **Rows left out.** 40 sales under $10,000 are left out, as the description sheet suggests for its impossible prices. The page states this count and computes it when it loads. No other rows are removed.
- **Not the sheet's $1,000 cutoff.** The description sheet's medians use sales of $1,000 or more. This site uses $10,000, so a few medians differ by a small amount. Ann Arbor's median is $572,000 here and $571,000 in the sheet.
- **Five things that will bite you, and what the site did about each one:**
  1. *Days on market.* The site does not use listing or contract dates, so the blanks in those columns do not affect it.
  2. *Street addresses are not unique.* The site does not use addresses. It counts sales by city and never removes rows that share an address.
  3. *Impossible prices.* Handled by the $10,000 cutoff above.
  4. *`home_type` is unreliable.* The site does not use it.
  5. *Impossible areas and lot sizes.* The site does not use living area or lot size.
- **Campus names** come from the `university` column. Each city maps to one campus in the data.
- **Prices are purchase prices, not rents.** The page says this, so a student does not read a sale price as a monthly cost.

## Tools we used

- **AI coding agent:** Claude Code, which wrote and edited the site under the instructions in `AGENTS.md`.
- **Site:** plain HTML, CSS and JavaScript, with no libraries and no build step. The page reads the CSV in the visitor's browser.
- **Publishing:** GitHub Pages, through `.github/workflows/pages.yml`.
- **Checks:** Python 3 and Node.js, run in the agent's environment to recompute the city medians and the excluded count from the CSV and compare them with the page's logic. No browser test was completed.

## Citation

College-town home sales dataset, version 1.0 (2026). University of Illinois-Deloitte Foundation Center for Business Emerging Technologies. Data collected March 2026.

## Who did what

The repository owner set the question and checked each change. An AI coding agent (Claude Code) wrote the page and this README, working from the owner's instructions in `AGENTS.md`.
