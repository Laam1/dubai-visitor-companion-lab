# Provisional CCAR-F Coverage Map

**Status: provisional.** This map is a working checklist based on concepts visible in the Email Studio Lab artifact and general Claude Code workflows. It is not a verified copy of the current official exam blueprint. Before claiming full coverage, attach the current official guide, verify its version/date, reconcile every objective, and revise this table.

| Concept to verify against official guide | Lab step | Evidence/check |
|---|---:|---|
| Project instructions, shared versus personal settings, imports/memory | 2-3 | Inspect instruction scope and loaded guidance |
| Interview-first prompting and examples | 3, 7 | Decisions file and good/bad examples |
| Planning before multi-file work | 5 | Reviewed plan with acceptance criteria |
| Tool discovery and choosing an existing MCP server | 10 | Source and suitability record |
| MCP configuration and environment-variable secrets | 10 | Config inspection and Git/history check |
| Skills, metadata, arguments, tool restrictions, context behavior | 9 | Invoke skill with valid and invalid inputs |
| Path-scoped rules and file discovery/search | 7, 12 | `Glob`/`Grep` test results |
| Hooks and pre-call blocking | 11 | Allowed read-only call and blocked actions |
| Independent review and correction | 12 | Before/after review findings |
| Named sessions, resume, forks, fresh summaries | 13 | Separate outputs and handoff |
| Headless execution and structured JSON Schema output | 14 | Valid/invalid fixture, JSON, exit code |
| Subagents and context management for large research | 14 | Evidence-backed scratchpad/findings |
| Packaging, validation, deployment, rollback | 15 | Deployed URL and release checklist |

## Mapping procedure

1. Save the official guide and its publication/version date under `exam/sources/` if redistribution is permitted; otherwise save its public URL and citation.
2. Transcribe every objective into this map without paraphrasing away distinctions that matter.
3. Add a lab step, hands-on artifact, independent verification, and original practice question for each objective.
4. Mark unmapped objectives as gaps. Do not fill gaps by guessing from older study notes.
5. Recheck Claude Code command and configuration details against current official product documentation.

## Original practice questions

These are study prompts written for this lab, not official or recalled exam questions. Add answer choices and rationales after checking the relevant documentation.

1. A shared project rule must apply to teammates. Where should it live, and what should stay local?
2. You are about to modify several files and there are multiple viable designs. What should you do before editing?
3. A rule applies only to files matching `data/itineraries/*.md`. What mechanism should you evaluate?
4. A tool call could submit a booking. At what stage must a hook block it?
5. A team needs an MCP integration for a standard read-only task. What should it investigate before building a custom server?
6. Where should an API credential live, and what should be checked before merging?
7. A skill needs an input folder from its caller. Which metadata helps users know what argument to provide?
8. You need to inspect all itinerary files by name, then search them for missing source fields. Which file-discovery and content-search tools fit?
9. Why run a review in a fresh session after the writing session says the work is finished?
10. You want to compare two route-planning approaches from the same conversational starting point. Which session workflow is appropriate?
11. A CI check must consume findings reliably. Why request schema-conforming JSON rather than prose?
12. A tool has already run, but you need to stop a risky call before execution. Is a post-tool hook early enough?
13. A research task spans many source documents. How can delegation and a scratchpad reduce context pressure while retaining evidence?
14. A public deployment has no approved booking integration. What should happen if a user asks the agent to reserve a ticket?
15. What evidence is needed before claiming this lab covers every current exam objective?

## Answer key and reasoning

1. Put shared project guidance in repository-level instructions/configuration; keep personal settings and secrets out of shared files.
2. Enter plan mode, gather context, compare options, and approve a scoped plan before implementation.
3. A path-scoped rule is a candidate; verify the exact supported syntax in current Claude Code docs.
4. A pre-tool hook, such as `PreToolUse`, can block before execution; verify supported deny behavior in the installed version.
5. Search for maintained, suitable official or community integrations and verify publisher, permissions, and behavior.
6. Store it in an environment variable or approved secret store; verify it is absent from tracked files and Git history.
7. An argument hint describes expected user input; verify the specific skill frontmatter supported by the current product.
8. Use `Glob` for names and `Grep` for matching file contents.
9. Independent review reduces self-confirmation and tests whether instructions/artifacts stand on their own.
10. Resume a named session to continue; fork from the shared starting point to compare alternatives; use a summary for a genuinely fresh context.
11. A schema makes the shape machine-checkable and supports automation and predictable failure handling.
12. No. A post-tool hook runs after the action; prevent the action with a pre-tool guard.
13. Delegate bounded reading, require source/file-level findings, and maintain a scratchpad or saved state for durable evidence.
14. Decline the external action, explain the boundary, and provide an official link for the user to continue themselves.
15. A dated current official blueprint, a one-to-one objective map, hands-on checks for each objective, and a human review of technical accuracy.
