# GitHub Copilot Agents

A collection of custom GitHub Copilot **flows** for VS Code. Each flow is a self-contained folder bundling its own agents and slash-command prompt, so you can keep many independent flows side by side.

## Structure

```
github-copilot-agents/
├─ .vscode/
│  └─ settings.json          # registers flows/**/agents and flows/**/prompts
└─ flows/
   └─ career-advisory-board/ # one folder per flow
      ├─ agents/             # *.agent.md (the personas / subagents)
      ├─ prompts/            # *.prompt.md (the slash command that orchestrates them)
      └─ README.md           # docs for this flow
```

Each **flow** = one folder under `flows/`. Inside, `agents/` holds any number of `*.agent.md` personas, and `prompts/` holds the `*.prompt.md` command(s) that orchestrate them.

## How discovery works

`.vscode/settings.json` registers the flow folders with **glob patterns**:

```jsonc
{
  "chat.agentFilesLocations":  { "flows/**/agents":  true },
  "chat.promptFilesLocations": { "flows/**/prompts": true }
}
```

Because these are globs, **every flow you add under `flows/` is discovered automatically** — no settings changes needed.

## Adding a new flow

1. Create `flows/<your-flow>/agents/` and `flows/<your-flow>/prompts/`.
2. Add one or more `*.agent.md` files in `agents/`.
3. Add a `*.prompt.md` in `prompts/` — its filename becomes the slash command (e.g. `my-flow.prompt.md` → `/my-flow`).
4. Reload VS Code (**Developer: Reload Window**). Done.

## Flows

| Flow | Command | What it does |
|------|---------|--------------|
| [career-advisory-board](flows/career-advisory-board/) | `/career-advisory-board` | A board of leader personas deliberate a problem and return a consensus position |

> Persona agents are simulations of public figures for deliberation purposes, not the real individuals.

## Using these in other workspaces

The `.vscode/settings.json` here works when this repo is your open workspace. To use the flows from any workspace, add the same keys to your **User Settings (JSON)** with absolute paths, e.g.:

```jsonc
{
  "chat.agentFilesLocations":  { "/Users/amit_sinha/development/github-copilot-agents/flows/**/agents":  true },
  "chat.promptFilesLocations": { "/Users/amit_sinha/development/github-copilot-agents/flows/**/prompts": true }
}
```
