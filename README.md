# Conqueror Agent Skills

SEO workflows for Claude Code, Codex, and other AI agents that support `SKILL.md`.

Each skill hands your agent one repeatable job — find keywords worth targeting, map them to pages, study a competitor, rewrite a page to win a term — using live data from [Conqueror](https://conquerorapp.com).

## Connect Conqueror MCP first

**These skills do nothing on their own.** They tell your agent which workflow to run; the data comes from the Conqueror MCP server. Connect it before installing anything:

```
https://winwith.conquerorapp.com/mcp
```

In Claude Desktop or Claude Code, add that as a remote MCP server and sign in when prompted. You need a Conqueror account — [start free](https://conquerorapp.com).

## Install

```sh
npx skills add Shipper-dot-now/conqueror-skills
```

Pick the skills and agents you want interactively, or take everything:

```sh
npx skills add Shipper-dot-now/conqueror-skills --skill '*'
```

Scope it to one agent with `--agent claude-code` or `--agent codex`.

To install by hand instead, copy the folders into your agent's skills directory:

```sh
git clone https://github.com/Shipper-dot-now/conqueror-skills.git

mkdir -p ~/.claude/skills && cp -R conqueror-skills/skills/* ~/.claude/skills/   # Claude Code
mkdir -p ~/.codex/skills  && cp -R conqueror-skills/skills/* ~/.codex/skills/    # Codex
```

## The skills

Start here if you're new:

| Skill | What it does |
| --- | --- |
| `/conqueror-seo-project-setup` | Sets up a durable local workspace — working folder, site scope, goals, positioning, and Search Console intake — so your agent keeps context between sessions. |
| `/conqueror-seo-coach` | Explains what each workflow does and recommends the next step. Use it when you're not sure what to run. |

Research:

| Skill | What it does |
| --- | --- |
| `/conqueror-keyword-research` | Turns seed topics into a prioritized opportunity set, scored on volume, difficulty, intent, and SERP reality. |
| `/conqueror-keyword-clustering` | Groups keywords into page-level clusters, maps each to an existing or new page, and flags cannibalization. |
| `/conqueror-competitive-landscape` | Maps who wins a market, which content is working, and where the openings are. |
| `/conqueror-competitor-analysis` | Deep dive on one competitor — ranking keywords, content themes, backlinks, weaknesses. |

Act on it:

| Skill | What it does |
| --- | --- |
| `/conquer-keyword` | Rewrites your WordPress site's best-matching page for a target keyword and proposes it as a diff you review before anything goes live. Needs a WordPress connection. |
| `/conqueror-link-prospecting` | Finds link prospects from SERPs and competitor backlinks, digs out public contact paths, and drafts the outreach. |

## How they work

A skill is a markdown file. Your agent reads it when you run the matching slash command, then follows the workflow using the Conqueror MCP tools it describes. Nothing is compiled or executed — you can read every one of these files in a couple of minutes, and you should.

The skills never publish, apply, or spend on your behalf without asking. `/conquer-keyword` proposes a diff; applying it is your click in Conqueror.

To learn how skills work in your agent:

- [Claude Code skills documentation](https://docs.claude.com/en/docs/claude-code/skills)
- [OpenAI Skills documentation](https://help.openai.com/en/articles/20001066-skills-in-chatgpt)

## As a plugin

The repo is also a plugin (`.claude-plugin/plugin.json`): installing it adds these skills and the Conqueror MCP server in one step, in agents that read that manifest, such as Claude Code and Grok Build.

## Network and credentials

The plugin talks to one endpoint, the Conqueror MCP server at `https://winwith.conquerorapp.com/mcp` (`.mcp.json`). It signs in with OAuth against your Conqueror account in the browser. No API keys, tokens or environment variables are read, and the skills run no scripts.

## License

MIT — see [LICENSE](LICENSE).
