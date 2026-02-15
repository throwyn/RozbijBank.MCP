# RozbijBank MCP Server

[Model Context Protocol](https://modelcontextprotocol.io) server for [RozbijBank](https://rozbijbank.pl) — Poland's bank comparison platform.

Gives AI assistants real-time access to Polish bank accounts, savings, deposits, promotions, referral codes, and financial calculators.

**Server URL:** `https://mcp.rozbijbank.pl/`

**Transport:** Streamable HTTP

## Quick Start

Add to your MCP client configuration:

```json
{
  "mcpServers": {
    "rozbijbank": {
      "url": "https://mcp.rozbijbank.pl/"
    }
  }
}
```

### Client Setup

| Client | How to connect |
|--------|---------------|
| **Claude Desktop** | Settings → Developer → Edit Config → add the JSON above to `claude_desktop_config.json` |
| **Claude.ai** | Settings → Integrations → Add MCP Server → paste URL |
| **Claude Code** | `claude mcp add rozbijbank --transport http https://mcp.rozbijbank.pl/` |
| **Cursor** | Settings → MCP → Add Server → type `http`, paste URL |
| **Windsurf** | Settings → MCP → Add Server → paste URL |
| **VS Code (Copilot)** | Settings → MCP → add to `mcp.json` |

## Available Tools

### Bank Offers

| Tool | Description | Key Parameters |
|------|-------------|----------------|
| `SearchPersonalAccounts` | Compare personal bank accounts — fees, features, rewards, scores | `bankName`, `minScore`, `featureName`, `sortBy`, `limit` |
| `SearchSavingsAccounts` | Compare savings accounts — interest rates, conditions | `bankName`, `minInterestRate`, `noCheckingRequired`, `sortBy`, `limit` |
| `SearchDeposits` | Compare deposits — rates by amount, period, currency | `bankName`, `currency`, `period`, `minInterestRate`, `sortBy`, `limit` |
| `SearchBusinessAccounts` | Compare business accounts for JDG and companies | `bankName`, `customerType`, `minScore`, `sortBy`, `limit` |

### Promotions

| Tool | Description | Key Parameters |
|------|-------------|----------------|
| `SearchPromotions` | Search active bank promotions | `productTypes`, `bankNames`, `sort`, `page`, `pageSize` |
| `GetPromotionDetails` | Full details: tasks, hidden fees, traps, expert recommendation | `promoId` |

Product types: `personalAccount`, `savingsAccount`, `deposit`, `businessAccount`, `creditCard`, `personalVipAccount`

### Utilities

| Tool | Description |
|------|-------------|
| `GetBanks` | List all available banks with logos |
| `GetReferralCode` | Get a referral/invitation code for a bank |
| `GetBlogArticles` | Published financial guides and articles |
| `GetPlatformStatistics` | Platform stats: users, promotions, total earnings |
| `CalculateDepositInterest` | Calculate net interest after Belka tax (19%) |

## Example Prompts

- "What is the best savings account in Poland right now?"
- "Compare personal accounts from mBank and ING"
- "Show me bank promotions ending this week"
- "Calculate interest on a 50,000 PLN deposit at 6% for 12 months"
- "Get a referral code for mBank"
- "What are the best business accounts for sole proprietorship?"
- "Are there any promotions with cashback for credit cards?"

## Tech Stack

- .NET 8.0 / ASP.NET Core
- [ModelContextProtocol C# SDK](https://github.com/modelcontextprotocol/csharp-sdk)
- Streamable HTTP transport
- SQL Server database

## Links

- **Website:** [rozbijbank.pl](https://rozbijbank.pl)
- **MCP Server:** [mcp.rozbijbank.pl](https://mcp.rozbijbank.pl/)
- **Blog:** [rozbijbank.pl/blog](https://rozbijbank.pl/blog)
- **Smithery:** [https://smithery.ai/servers/rozbijbank/rozbijbank](https://smithery.ai/servers/rozbijbank/rozbijbank)

## License

This is a hosted MCP server. The source code is proprietary. This repository serves as documentation and a public entry point for MCP directory listings.
