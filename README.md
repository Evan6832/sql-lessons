# SQL Lessons — Disney Edition

A hands-on, Disney-themed intro to SQL for analysts and customer success teammates who are new to coding. Reading and querying focused — you'll write `SELECT` queries against a small Disney universe (princesses, movies, characters, parks, attractions).

We use **GoogleSQL** (BigQuery's modern dialect) and run everything in **Google Colab** — free, browser-based, no install.

---

## Open a lesson in Colab

Click a badge to open the lesson in Colab. **Always come back to this page** to start a lesson — clicking a badge here always opens the latest version.

| # | Lesson | What you'll learn | Open |
|---|--------|-------------------|------|
| 00 | What is SQL? | Database, table, row, column | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Evan6832/sql-lessons/blob/main/00_concepts.ipynb) |
| 01 | Your first query | `SELECT`, `FROM`, `LIMIT` | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Evan6832/sql-lessons/blob/main/01_first_query.ipynb) |
| 02 | Filtering | `WHERE`, `AND`/`OR`, `IN`, `BETWEEN`, `LIKE` | _coming soon_ |
| 03 | Sorting & DISTINCT | `ORDER BY`, `DISTINCT` | _coming soon_ |
| 04 | Aggregations | `COUNT`, `SUM`, `AVG`, `MIN`, `MAX` | _coming soon_ |
| 05 | Grouping | `GROUP BY`, `HAVING` | _coming soon_ |
| 06 | Joins | `INNER JOIN`, `LEFT JOIN` | _coming soon_ |
| 07 | Conditional logic | `CASE WHEN` | _coming soon_ |
| 08 | Dates | Date functions in GoogleSQL | _coming soon_ |
| 09 | Capstone | Putting it all together | _coming soon_ |

Work through them in order — each builds on the last.

## Tips for using Colab notebooks

- **Run a cell** with `Shift+Enter`, or click the ▶ play button on its left.
- **Colab autosaves your work** to your Google Drive — you won't lose your exercises if you close the tab.
- **Coming back later?** Click `Runtime → Restart and run all` to re-run the setup cell and pick up where you left off.
- **Use Chrome** for the smoothest experience (especially for the Google sign-in popup).
- **Sign in with the email** your project lead invited you with. If your queries fail with permission errors, that's almost always why.

## What you can and can't do

By design, the learner has minimal permissions:

| ✅ Can | ❌ Cannot |
|--------|-----------|
| Run `SELECT` queries against the practice tables | Create, modify, or delete tables |
| Read all columns of `disney_lessons` tables | See any other dataset in the project |
| Re-run queries as many times as you want | See billing, costs, or budgets |
| Experiment freely without breaking anything | Touch any other GCP service |

If you try to do something outside your permissions, BigQuery returns a clear error. Nothing destructive is possible.

---

## Admin track (project lead, one-time setup)

This section is for the person setting up the tutorial — not the learner.

### 1. Create or pick a BigQuery project

Visit <https://console.cloud.google.com/bigquery>. Create a project (e.g. `sql-with-disney`) or reuse an existing one.

If your project has billing attached (orange "incurring charges" banner), that's fine. The lesson queries process tiny amounts of data and stay well within BigQuery's 1 TB/month free tier — real cost will be effectively $0.

### 2. Verify the BigQuery API is enabled

Open <https://console.cloud.google.com/apis/library/bigquery.googleapis.com>. If you see "Enable," click it. If you see "Manage," you're good. (On most projects this is on by default.)

### 3. Run the admin setup notebook

[![Open admin setup in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Evan6832/sql-lessons/blob/main/_admin_setup.ipynb)

Edit the configuration cell:
- `PROJECT_ID` — your BigQuery project ID (e.g. `sql-with-disney`)
- `COLLEAGUE_EMAIL` — your colleague's Google email (leave empty if you're testing solo first)

Run all cells. The notebook will:
- Create the `disney_lessons` dataset
- Load the practice tables (currently `princesses` — more added with future lessons)
- Grant your colleague **BigQuery Data Viewer** on `disney_lessons`

### 4. Grant the BigQuery Job User role in the Console

The admin notebook prints a direct link. The 4 clicks:

1. Open the printed link (`console.cloud.google.com/iam-admin/iam?project=...`)
2. Click **+ GRANT ACCESS**
3. Paste your colleague's email
4. Role: **BigQuery Job User** → **SAVE**

### 5. Share this README

Send your colleague the link to this GitHub repo. She'll click the badges in the lesson table to open lessons.

---

## Practice data

All practice tables live in `disney_lessons` in your BigQuery project:

| Table | Loaded by | Used in lessons |
|-------|-----------|-----------------|
| `princesses` | Admin notebook (now) | 01–05 |
| `movies` | Admin notebook (future) | 04+ |
| `characters` | Admin notebook (future) | 06+ |
| `parks` | Admin notebook (future) | 08+ |
| `attractions` | Admin notebook (future) | 06+ |

When new lessons drop that need additional tables, update the admin notebook and re-run.
