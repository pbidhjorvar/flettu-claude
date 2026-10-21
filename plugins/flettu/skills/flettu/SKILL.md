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

1. **Find the company.** `search_companies` with a name or kennitala. Pick the
   right match by name and kennitala; if several fit, ask the user which one.
2. **Read it.** `get_company` for the profile, `get_company_timeline` for status
   and history, `get_financials` for figures by year.
3. **Compare or screen.** `create_comparison` (two to ten companies, several
   years) or `screen_companies` / `screen_companies_by_attributes` for a
   filtered list. Use `discover_company_attributes` and `get_metric_catalog`
   first to learn what can be filtered and how metrics are defined.
4. **Show the source.** For any figure the user will rely on, call
   `get_report_evidence` and cite the document and page.
5. **Export.** `export_research` with `format` xlsx, pdf, csv or json when the
   user wants a file.

## Cost

Searching, company profiles, financials, comparisons, research packages and
screens use a small amount of the account's credit. Source pages, the company
history, metric definitions, pricing, saved results and exports are free.
Before a larger job (`build_research`, `create_comparison` or a screen), call
`get_research_pricing`, tell the user what it costs, and go ahead when they
agree. `get_account_usage` shows the balance.

## How to present results

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
