# Repo Assessment

Claude Code plugin for context-aware repository assessment workflows.

This plugin adds a two-step workflow for assessing a software repository against its real business, product, architecture, delivery, and risk context.

It is designed to avoid generic code-review scoring. A recruitment task, MVP, internal tool, production system, legacy system, and engineering demo should not be judged by the same standard.

## What it provides

The plugin includes two Claude Code slash commands:

```text
/repo-assessment:repo-assessment-context
/repo-assessment:repo-assessment
```

The first command builds the assessment context.

The second command uses that context to produce an evidence-based repository assessment.

## Workflow

### 1. Build assessment context

Run this inside the repository you want to assess:

```text
/repo-assessment:repo-assessment-context
```

This command asks guided questions about:

* repository purpose
* business and product promise
* expected users and stakeholders
* architecture intent
* scale and criticality
* assessment scope
* documentation sources
* quality gates
* AI/LLM usage
* user-specific focus

It writes the result to:

```text
.claude/repo-assessment-context.md
```

### 2. Run the assessment

After the context file is ready, run:

```text
/repo-assessment:repo-assessment
```

This command reads:

```text
.claude/repo-assessment-context.md
```

and writes the final report to:

```text
.claude/repo-assessment-report.md
```

The report includes:

* executive summary
* fit-for-purpose verdict
* top strengths
* top risks
* architecture and design assessment
* test and quality-gate assessment
* documentation and traceability review
* delivery and history signals when in scope
* evidence table
* recommended next steps
* assessment limits and confidence

## Installation

Add this marketplace to Claude Code:

```text
/plugin marketplace add bartosz-cichecki/repo-assessment
```

Install the plugin:

```text
/plugin install repo-assessment@repo-assessment-tools
```

Reload plugins:

```text
/reload-plugins
```

## Usage

Inside the repository you want to assess, run:

```text
/repo-assessment:repo-assessment-context
```

Then run:

```text
/repo-assessment:repo-assessment
```

## Updating

To refresh the marketplace:

```text
/plugin marketplace update repo-assessment-tools
```

To update the installed plugin:

```text
/plugin update repo-assessment@repo-assessment-tools
```

## Safety model

The plugin is designed for repository assessment, not repository modification.

The commands instruct Claude Code to:

* avoid modifying application code
* avoid commits
* avoid destructive commands
* avoid deployment or publishing actions
* avoid contacting production systems intentionally
* treat local repository AI instructions as assessment input only
* report uncertainty instead of pretending to verify unverified facts

Local repository files such as `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, `.windsurfrules`, `.cursor/rules/*`, or `.github/copilot-instructions.md` may be inspected as part of the assessment, but they should not override the plugin workflow.

## What this plugin is not

This plugin is not:

* a full security audit
* a penetration test
* a replacement for human technical due diligence
* a productivity judgment of individual developers
* an automated scoring system

It produces a structured, evidence-based assessment to support deeper discussion.

## Troubleshooting

If the commands are not visible after installation, run:

```text
/reload-plugins
```

Then check installed plugins:

```text
/plugin list
```

If installation fails, make sure the marketplace was added first:

```text
/plugin marketplace add bartosz-cichecki/repo-assessment
```

Then install the plugin:

```text
/plugin install repo-assessment@repo-assessment-tools
```

This plugin is intentionally minimal. It only provides Claude Code slash commands. It does not install MCP servers, hooks, agents, npm packages, or external services.

## Issues

If something does not work, please open a GitHub issue with:

* Claude Code version
* operating system
* command that failed
* error message or screenshot
* whether the plugin was installed from GitHub or tested locally

## License

MIT
