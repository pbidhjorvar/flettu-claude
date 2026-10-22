---
name: flettu
description: Research Icelandic companies with Flettu — find a company by name or kennitala, read its sourced annual-report figures, compare companies, screen an industry, and cite the source page. Use when the user asks about an Icelandic company, its revenue, profit, equity, owners, board or industry, mentions a kennitala, ársreikningur, fyrirtæki, ehf. or hf., or asks to compare or list Icelandic companies.
---

# Flettu: Icelandic company research

Flettu (flettu.is) holds Icelandic companies' registry facts and annual-report
figures with their sources. The `flettu` connector's tools read that data. The
first call opens a browser to sign in with a Flettu account; after that it
just works.

## The workflow

1. **Lists, rankings and totals across companies:** `query_companies`. The
   largest by revenue, most profitable, most employees, fastest growth, a town,
   an industry (ÍSAT), a legal form or a founding decade; filters on any
   figure; totals per industry, town or legal form (a group counts once).
   Amounts are ISK; foreign filers are converted at the year's average rate.
2. **One company:** `search_companies` with a name or kennitala, then
   `get_company` (profile, group, key figures) and `get_financials` (every
   figure by year with change from the year before). If several companies
   fit a name, ask the user which one.
3. **Compare:** `compare_companies` (two to ten companies, chosen years).
4. **Show the source.** For a figure read from a filed report, call
   `get_report_evidence` and cite the document and page.
5. **Export.** `export_research` with `format` xlsx, pdf, csv or json when the
   user wants a file.

## Cost

Flettu is in beta and free to use.

## How to present results

- **Groups.** Rows say when a company belongs to a larger group
  (`part_of_group`); mention it when a parent and its subsidiary both appear.
- **Unusual figures.** When a row is flagged `unusual`, say the profit likely
  includes one-off items.
- **Missing is not zero.** When a figure is missing, say it is missing. Never
  treat it as 0 or estimate it.
- **Say what the number is.** Give the year, unit and scope (company or group)
  with every figure, and say when a figure is provisional or unverified.
- **Icelandic formatting.** Amounts in millions of krónur as `502 m.kr.`,
  billions as `1,6 ma.kr.`; decimal comma, full stop for thousands (`13.196`).
- **Kennitala** as `541205-1520`.
- **Link** each company to its page on Flettu:
  `https://flettu.is/leit?view=company&company=<kennitala>`.
- **People** with the same name can be different people. Where Flettu gives a
  birth month, use it to tell them apart; otherwise say the records may cover
  more than one person.

## When the data is not there yet

If a company or year has not been collected yet, `get_company` and
`get_financials` queue it for collection. Tell the user it is being fetched and
offer to look again in a little while.
