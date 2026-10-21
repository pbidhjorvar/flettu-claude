# Flettu for Claude

Icelandic company data in Claude: search companies, read sourced annual-report
figures, compare companies and screen industries. You sign in with your
[Flettu](https://flettu.is) account the first time Claude uses it.

## Claude Code

```
/plugin marketplace add pbidhjorvar/flettu-claude
/plugin install flettu@flettu
```

Then ask, for example: *Hver var velta Bruggsmiðjunnar Kalda 2021–2025?* The
first question opens a browser to sign in.

## Claude (web, desktop and mobile)

Open [Flettu in the Claude Connectors Directory](https://claude.ai/directory/connectors/flettu),
select **Connect** and sign in to Flettu. The connector follows your Claude
account to Claude Desktop and the mobile app.

## What is included

- **Connector**: Flettu's MCP server at `https://flettu.is/api/mcp` (OAuth sign-in).
- **Skill** `flettu`: how to research a company, compare and cite sources,
  and how to present Icelandic figures.

Searches, company figures, comparisons and screens use a small amount of your
Flettu credit; Claude tells you the price before larger jobs. Source pages and
exports are free.

Help: [flettu.is/tengingar](https://flettu.is/tengingar) · flettu@flettu.is
