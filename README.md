# GitHub Copilot Agents

A collection of custom GitHub Copilot **flows** for VS Code. Each flow is a self-contained folder bundling its own agents and slash-command prompt, so you can keep many independent flows side by side.

## Structure

```
github-copilot-agents/
├─ .vscode/
│  └─ settings.json          # registers each flow's agents/ and prompts/ folder (literal paths)
└─ flows/
   └─ career-advisory-board/ # one folder per flow
      ├─ agents/             # *.agent.md (the personas / subagents)
      ├─ prompts/            # *.prompt.md (the slash command that orchestrates them)
      └─ README.md           # docs for this flow
```

Each **flow** = one folder under `flows/`. Inside, `agents/` holds any number of `*.agent.md` personas, and `prompts/` holds the `*.prompt.md` command(s) that orchestrate them.

## How discovery works

`.vscode/settings.json` registers each flow's folders with **literal paths**:

```jsonc
{
  "chat.agentFilesLocations": {
    "flows/career-advisory-board/agents": true,
    "flows/college-admissions-advisor/agents": true
  },
  "chat.promptFilesLocations": {
    "flows/career-advisory-board/prompts": true,
    "flows/college-admissions-advisor/prompts": true
  }
}
```

> **Important:** these two settings do **not** support glob keys. VS Code rejects any key
> containing `*`, `?`, `[`, `]`, `{`, or `}` (silently — no error), so `flows/**/agents`
> never loads. They also **do not** scan subfolders recursively for `*.agent.md` /
> `*.prompt.md`, so you can't point at a parent folder either. Each flow's `agents/` and
> `prompts/` folder must be listed explicitly.

## Adding a new flow

1. Create `flows/<your-flow>/agents/` and `flows/<your-flow>/prompts/`.
2. Add one or more `*.agent.md` files in `agents/`.
3. Add a `*.prompt.md` in `prompts/` — its filename becomes the slash command (e.g. `my-flow.prompt.md` → `/my-flow`).
4. **Register the new folders** by adding `flows/<your-flow>/agents` and `flows/<your-flow>/prompts` to the two settings blocks in `.vscode/settings.json`.
5. Reload VS Code (**Developer: Reload Window**). Done.

## Flows

| Flow | Command | What it does |
|------|---------|--------------|
| [career-advisory-board](flows/career-advisory-board/) | `/career-advisory-board` | A board of leader personas deliberate a problem and return a consensus position |
| [college-admissions-advisor](flows/college-admissions-advisor/) | `/college-admissions-advisor` | An agent with subagents acting as a college advisor for university in the US |

> Persona agents are simulations of public figures for deliberation purposes, not the real individuals.

## Using these in other workspaces

The `.vscode/settings.json` here works when this repo is your open workspace. To use the flows from any workspace, add the same keys to your **User Settings (JSON)** with absolute, per-flow paths (no globs), e.g.:

```jsonc
{
  "chat.agentFilesLocations": {
    "/<path to folder>/github-copilot-agents/flows/career-advisory-board/agents": true,
    "/<path to folder>/github-copilot-agents/flows/college-admissions-advisor/agents": true
  },
  "chat.promptFilesLocations": {
    "/<path to folder>/github-copilot-agents/flows/career-advisory-board/prompts": true,
    "/<path to folder>/github-copilot-agents/flows/college-admissions-advisor/prompts": true
  }
}
```
