# Codex SignalPilot Plugin

Governed AI database access for dbt and SQL with sandboxed queries, schema discovery, and intelligent model building powered by [SignalPilot](https://signalpilot.ai).

## Install

### Step 1: Connect the MCP server

```bash
# Cloud
codex mcp add --transport http signalpilot https://gateway.signalpilot.ai/mcp \
  --header "Authorization: Bearer sp_YOUR_API_KEY"

# Local / self-hosted
codex mcp add --transport http signalpilot http://localhost:3300/mcp
```

### Step 2: Install the plugin

```bash
codex plugin marketplace add SignalPilot-Labs/codex-signalpilot-plugin
codex plugin add signalpilot@signalpilot
```

One-line install:

```bash
codex plugin marketplace add SignalPilot-Labs/codex-signalpilot-plugin && codex plugin add signalpilot@signalpilot
```

Step 1 gives you the SignalPilot MCP tools. Step 2 adds Codex skills on top.

## What's Included

### MCP Tools

| Category | Tools |
|----------|-------|
| Schema Discovery | `schema_overview`, `list_tables`, `describe_table`, `explore_table`, `explore_column`, `explore_columns`, `get_relationships`, `schema_ddl`, `schema_link` |
| Querying | `query_database`, `validate_sql`, `explain_query`, `estimate_query_cost` |
| Analysis | `analyze_grain`, `schema_statistics`, `find_join_path`, `compare_join_types`, `get_date_boundaries`, `schema_diff` |
| Governance | `check_budget`, `query_history`, `audit_model_sources`, `validate_model_output` |
| Infrastructure | `list_database_connections`, `connection_health`, `connector_capabilities` |

### Skills

| Skill | Description |
|-------|-------------|
| `signalpilot` | Main entry point for schema discovery and governed queries |
| `sql-workflow` | Structured SQL query building with verification |
| `dbt-workflow` | Full dbt project workflow for scan, map, validate, write, and verify |
| `dbt-write` | dbt model writing with column naming and type rules |
| `dbt-debugging` | Fix dbt run and parse failures |
| DB-specific | `bigquery-sql`, `snowflake-sql`, `duckdb-sql`, `sqlite-sql` |

## Requirements

- Codex CLI with plugin support
- A SignalPilot account or a self-hosted SignalPilot gateway

## License

Apache-2.0
