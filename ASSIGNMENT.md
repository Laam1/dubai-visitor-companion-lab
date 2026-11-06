# Dubai Visitor Companion Lab

Build a source-grounded, one-day Dubai itinerary assistant, test it with people, and deploy a clearly labeled demo. This lab teaches Claude Code through the project. Its exam map is provisional: use the current official CCAR-F guide as the authority before claiming complete exam coverage.

## Definition of done

- A visitor can enter a time window, starting area, interests, budget, pace, language, and optional mobility needs.
- The agent returns a practical itinerary with reasons, travel transitions only when supported, source links, freshness notes, and alternatives.
- Unknown or stale facts are labeled and linked to official sources; accessibility is never guessed.
- The demo cannot book, pay, submit forms, or message venues.
- An independent test session checks the behavior and reports measured results.
- A small user test records task completion, time, satisfaction, trust, and factual accuracy.
- A public demo is deployed only after review, with no unnecessary visitor data retained.

## How each step works

Use a build prompt in Claude Code, inspect the proposed changes, then run the check prompt in a fresh session. Checks should verify files or behavior rather than ask Claude whether it complied. Keep a learning log with the command, result, and one-sentence explanation of the exam concept.

## Part 1: Find the problem and set up

### 1. Validate the problem
**Build:** Read `GOAL.md` and `research/market-evidence.md`. Create `research/interview-guide.md` and a blank `research/observations.csv` for the interview plan. Keep observed facts separate from assumptions. Add a dated source record for every statistic you plan to show.

**Check:** In a fresh session, list each claim in the evidence file, its source, date, and limitation. Flag claims that imply demand or satisfaction without user research. Do not change files.

**Exam checkpoint:** Which evidence supports market scale, and which evidence would actually validate the user problem?

### 2. Create the project workspace
**Build:** Initialize Git in this project folder if needed. Create the minimum folders for `agent/`, `data/`, `research/`, `tests/`, and `docs/`. Write a concise root `CLAUDE.md` describing the project, plain-language rules, source-grounding requirement, safety boundaries, and links to the goal and research files. Add a `.gitignore` for local secrets, environment files, and OS files. Do not add credentials.

**Check:** Run `git status`, `git check-ignore -v .env`, and inspect the root instructions. Report which instructions are shared and which local files are ignored.

**Exam checkpoint:** Where should team-wide project instructions live, and why should secrets not be committed?

### 3. Capture visitor needs before designing
**Build:** Ask the project owner one question at a time about target visitors, demo geography, supported languages, access needs, data freshness, and what must never be automated. Save confirmed decisions to `docs/product-decisions.md`; label unknowns instead of filling them in.

**Check:** In a fresh session, compare the decisions file with `GOAL.md`. Identify any unsupported assumption or contradiction without editing either file.

**Exam checkpoint:** Why interview first instead of immediately building from an incomplete request?

### 4. Map the current CCAR-F blueprint
**Build:** Create `exam/coverage.md` from the current official CCAR-F guide supplied by the learner. Map every official objective to a step, a hands-on task, and a check. Mark objectives with no exercise as gaps. Do not copy real exam questions; write original practice questions.

**Check:** Confirm every objective in the supplied guide appears in the map and every mapped objective has a verification task. Do not claim full coverage until a human checks the source version and mapping.

**Exam checkpoint:** What makes a coverage map auditable rather than a list of remembered topics?

## Part 2: Build the grounded agent

### 5. Plan the build
**Build:** Switch Claude Code to plan mode. Ask it to propose the smallest architecture for a local web demo using a versioned, curated source dataset. The plan must include data fields, citations, freshness handling, uncertainty behavior, safety controls, evaluation, and deployment. Do not build until the plan is reviewed and approved.

**Check:** Review the plan for external actions, unverified data dependencies, retention of personal data, and missing failure cases. Record accepted changes before implementation.

**Exam checkpoint:** When is plan mode appropriate, and what should happen before accepting its plan?

### 6. Build a source ledger
**Build:** Create `data/sources.csv` with source name, canonical URL, publisher, page title, checked date, fact supported, update frequency if known, and limitations. Add a small set of official tourism and transport facts only after opening and checking their sources. Never invent opening hours, prices, accessibility, or live schedules.

**Check:** Use a script or command to find entries with missing URLs, publisher, or checked date. Open each source and verify the corresponding fact. Report stale or unverifiable entries.

**Exam checkpoint:** How do provenance and freshness change the reliability of an agent's answer?

### 7. Add example-driven data rules
**Build:** Add two good and two bad itinerary examples to `data/examples/`. Create a folder-level `CLAUDE.md` for source records and a path-scoped rule for user-facing itinerary files. Require citations, uncertainty labels, and no fabricated access claims.

**Check:** Use `Glob` to find all itinerary files and `Grep` to find any missing source field or unsupported certainty phrase. Explain which rules applied to which paths.

**Exam checkpoint:** When should a path-scoped rule be used instead of putting every instruction in the root file?

### 8. Implement the demo experience
**Build:** Create a simple responsive web demo. Ask for the minimum planning inputs, generate one itinerary from the curated dataset, show sources and checked dates beside claims, and provide alternatives. Include a clear “verify before you go” state for changing details. Do not add accounts, booking, payments, analytics trackers, or live-location collection in the MVP.

**Check:** Run the app locally. Test one normal request, one request with missing information, one unsupported venue claim, and one mobility constraint. Verify that sources are visible and unknowns remain unknown.

**Exam checkpoint:** Why should the agent decline to make a confident claim when its source does not establish it?

### 9. Create a reusable planning skill
**Build:** Create a project skill such as `.claude/skills/plan-day/SKILL.md` with a clear name, description, argument hint, inputs, output schema, failure behavior, and tools it needs. Keep `context: fork` or restricted tool settings only when they help this task and are supported by the installed Claude Code version.

**Check:** Invoke the skill with valid, incomplete, and unsupported inputs. Confirm it stops or asks a question when required information is absent. Inspect the skill metadata and report which settings were actually used.

**Exam checkpoint:** What is the difference between a skill's description, argument hint, and allowed tools?

### 10. Add read-only tool access
**Build:** First search for a maintained, suitable MCP server or supported public API for any data that must be current. Record why it is appropriate. If none is suitable for the demo, keep the source ledger and do not invent a connector. Store any required credentials in environment variables, never in the repo.

**Check:** Inspect `.mcp.json` and the effective connection status. Verify that the configured server is read-only for this project and that no secret appears in Git-tracked files or history.

**Exam checkpoint:** When should a team reuse an existing MCP server, and where should credentials be stored?

### 11. Enforce action boundaries
**Build:** Add a `PreToolUse` hook that blocks booking, payment, account creation, messaging, and form-submission tools. Keep the user-facing instructions too, but do not rely on prose alone. Log only the blocked action category, not sensitive user input.

**Check:** Run safe tests showing a read-only lookup is allowed and each external action is blocked. Confirm the hook's exit/deny behavior and that `PostToolUse` is not being used as the blocker.

**Exam checkpoint:** Which hook stage can prevent a tool call before it runs?

## Part 3: Verify, package, and deploy

### 12. Review with fresh eyes
**Build:** In a new Claude Code session, ask for a severity-ranked review of the goal, source rules, itinerary outputs, and safety behavior. Fix related findings together, then record unresolved data questions for a human.

**Check:** Re-run the same review in a fresh session. Use `Glob` and `Grep` to verify every itinerary has citations and no external-action instructions. Do not accept “looks good” without evidence.

**Exam checkpoint:** Why is an independent session useful for reviewing work it did not create?

### 13. Compare approaches with session forks
**Build:** Resume a named research session and fork it twice to compare two planning strategies, such as shortest travel time versus fewer transitions. Save outputs separately and write a short handoff summary.

**Check:** Confirm each fork starts from the intended point, outputs do not claim access to the other fork's conversation, and shared files are not mistaken for shared conversation context.

**Exam checkpoint:** When should you resume a session, fork it, or start fresh with a summary?

### 14. Automate evaluation with structured output
**Build:** Create a JSON Schema for test findings and a headless review script that checks source presence, freshness fields, unsupported claims in fixtures, and action-boundary tests. Make failures machine-readable and fail the run on critical issues. Use a subagent for large source-catalog review only if it can return file-level evidence; maintain a scratchpad when processing many sources.

**Check:** Run the evaluator against one deliberately flawed fixture and one valid fixture. Verify both JSON shape and exit codes. Confirm a fresh rerun does not repeat resolved findings.

**Exam checkpoint:** Why use structured output and a schema in automation instead of free-form prose?

### 15. Deploy a controlled pilot
**Build:** Review hosting choices and select a simple deployment appropriate to the existing app. Publish a clearly labeled demo with a source/method note, privacy notice, feedback form that collects no sensitive details, and a rollback plan. Keep secrets server-side and prevent the demo from calling tools that can make bookings or send messages.

**Check:** Test the deployed URL on desktop and mobile. Verify citations, error handling, privacy behavior, and blocked actions. Run five exploratory user tests, record results in `research/pilot-results.md`, and decide go/revise/stop using the criteria in the research brief.

**Exam checkpoint:** What must be verified before moving a local prototype into a public pilot?

## Deliverables

- `GOAL.md` and `research/market-evidence.md`
- `exam/coverage.md` based on a dated official guide
- Root and path-specific Claude Code instructions
- Source ledger, examples, safety rule, and reusable skill
- Working local web demo, automated checks, and deployed pilot
- Interview notes with consent, pilot results, and a go/revise/stop decision

## Important exam note

This lab contains original practice questions, not official exam questions. Product behavior and exam wording may differ or change. Verify every objective and technical detail against the current official CCAR-F guide and current Claude Code documentation before calling the course exam-complete.
