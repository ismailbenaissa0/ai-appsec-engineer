---
name: efficient-ai-coding
description: Working habits for getting high-quality results on coding tasks while staying within free-tier usage limits and avoiding wasted prompts. Use this skill whenever the user is coding, building features, fixing bugs, refactoring, planning a task, writing tests, or setting up a project, and especially when they mention usage limits, prompt limits, request limits, context windows, slow or sloppy output, or want work done properly. Apply it by default on any non-trivial coding task, even if the user doesn't ask for efficiency.
---

# Efficient AI Coding

You are working with a developer who is using the free Codex tier, so the scarce resource is prompts, requests, or whatever their plan meters—not token billing. They also get worse results from you as your context fills up. So staying within limits, keeping context focused, and doing better work are the same goal. Follow the habits below on every coding task.

**Your core principle: only do what's necessary.** Read fewer files, load fewer tools, take smaller steps, keep context focused.

---

## 1. Before you touch any code

### Get specific, or ask

If a request is vague, you will end up reading the whole codebase to guess what the user wants. That wastes usage and produces worse results.

- If the request is ambiguous on a technical decision, ask one or two sharp questions before you start. Don't explore everything to guess.
- If the user names files, paths, or sources, use those and nothing else.
- State the goal and your definition of "done" in one or two lines before you begin.

### Don't go on research tangents

Every file you open and every page you fetch consumes context and may count against your usage limits.

- Read only what the task requires. Prefer targeted search (grep, symbol lookup) over opening whole files.
- If you catch yourself exploring files that don't bear on the task, stop and return to scope.
- Don't re-read or re-summarize things that are already in your context.

### Keep tasks small and separate

- Treat each task as its own session. A medium or large task can use a large share of a free-tier allowance, and research or skill loading can push you toward the limit.
- When the user starts an unrelated task in a long conversation, tell them it will go better in a fresh session, and offer a handoff summary.

---

## 2. Plan before big changes, not small ones

**Plan first when** the task touches many files, changes architecture, or would produce hundreds of lines.

**Skip planning when** the job is a typo, a rename, a copy or styling tweak, or a one-file change. Planning there wastes usage and doesn't improve the result.

A good plan:

- Lists the files you will change and why
- Notes risks and open questions
- Defines how you will verify success (see section 3)
- Is shown to the user for approval before you write any code

A mistake is far cheaper to catch in a plan than after it has spread across a dozen files.

**Model tiering:** if you are able to hand work to other models, use the strongest one for planning and a faster one for implementation. Modern fast models are capable enough for this to work well, and it can save usage.

---

## 3. Verify. Never assume.

This is the most important habit. You can't know your code works unless you check. **Never report a task as done because you wrote the code. Report it as done after you verify it.**

### Tests

- **Write the test first, then the implementation.** If you write the code first, you'll shape the tests to pass your own code, and that isn't testing.
- **Test what matters.** Cover core behavior, edge cases, and failure paths. Don't test every line. Over-testing bloats the codebase.
- Run the tests and read the actual output before you claim success.

### Static checks

- Run the type checker and linter, if the project has them, before you call anything done.
- Fix the errors. Don't suppress them.

### Front-end work

You can't see what you build. When you have the tools:

- Open the app in a browser, click through the flow, and check for errors.
- Take screenshots and look at them before you declare the UI finished.

### Definition of done

Before you finish, confirm that tests pass, types and lint are clean, behavior matches the request, and you changed nothing outside the scope.

---

## 4. Treat context as a limited working memory

Your context window is short-term memory. The more it holds, the more you forget, contradict yourself, and make dumb mistakes. Quality tends to dip noticeably after a long session, even if your window is much larger. A bigger window extends the weak zone; it doesn't remove it.

**Rules:**

1. **New task, new session.** Don't drag finished work into the next job.
2. **Watch your size.** Be aware of how much context you've used, especially before a large task. If you notice yourself getting inconsistent or forgetful, say so.
3. **Don't let yourself compact mid-task.** Auto-compaction in the middle of work loses details and hurts quality. If you're approaching the limit, wrap up the current step and suggest a fresh session instead.
4. **When you do compact, keep the essentials:** the goal, key decisions, files changed, and what's left to do.
5. **Hand off cleanly.** When a session is ending, write a short summary the user can paste into a new one: goal, decisions made, current state, next steps.
6. **Keep your output lean.** Don't repeat unchanged code. Show diffs or only the relevant section.

---

## 5. Be selective with skills and MCPs

### Skills

Skills are markdown guides for repeatable workflows, like code review, security review, house style, or a research method. Use the ones that fit the task. Don't load more than you need, because each one adds context.

If the user asks which skills to install, recommend a small set that matches their coding style and real workflows, not dozens. Useful categories are requirements refinement, architecture review, code-quality and simplification passes, security review, and planning with handoff to an implementer.

### MCPs (external tool connections)

Use an MCP **only when you must directly interact with something outside the codebase**: GitHub, a database, Slack, analytics, deployments, or a browser.

- Don't reach for an MCP to get best practices, patterns, or how-to knowledge. A skill or your own knowledge covers that.
- Good uses: fetching design inspiration, seeding a database with test data, reading live documentation, and browser testing.
- Use only what the current task needs.

---

## 6. Parallelism and automation: suggest when affordable

These raise quality and throughput but consume more usage. Match what you suggest to the user's plan.

| Technique                   | What it does                                                                                        | Usage / caution                                                                                                                     |
| --------------------------- | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| **Sub-agents**              | Specialist helpers (researcher, reviewer, debugger), each with its own context, returning a summary | Each is a full parallel conversation. On free or low-tier plans even a small setup can exhaust the limit. Great on high-tier plans. |
| **Worktrees**               | A separate folder per branch, so tasks run in parallel without interfering                          | Low usage and great for isolation. One chat per worktree works well.                                                                |
| **Loops / scheduled tasks** | Recurring automation                                                                                | Good for daily issue-to-PR work, security and bug sweeps, and feature brainstorming from the codebase and issues.                   |
| **Goal mode**               | Keep working until a condition is met (e.g. all tests pass, no type errors)                         | Worth it when the condition can be checked objectively.                                                                             |

If you don't know the user's plan or it looks limited, default to a single agent and small tasks. Don't spin up sub-agents unless asked or clearly worthwhile.

---

## 7. Respect and maintain the project memory file

If the project has a memory file (`CLAUDE.md`, `AGENTS.md`), follow it. If the user asks you to create or update one, keep it short and useful. It helps, but it isn't make-or-break, and skills can often do the same job.

**Put in it:**

- A quick description of the project
- Current status
- Coding style and conventions
- Quirks to avoid (for example, use sentence case in user-facing text, since AI tends to default to ALL CAPS)
- Pull request and commit preferences
- Working philosophy (e.g. "do only what's necessary", "verify before done")

**Leave out:** long architecture essays, full API docs, and anything you can find quickly with a search.

If a tool expects `AGENTS.md` but the project uses `CLAUDE.md`, import one from the other instead of duplicating.

Use this structure when creating one:

```markdown
# Project: <name>

## What this is
<2-3 sentences>

## Current status
<what works, what's in progress>

## Conventions
- Language/framework versions:
- Code style:
- User-facing text: sentence case, no ALL CAPS
- Pull requests: <preferred language/format>

## Working rules
- Plan first for big tasks; skip planning for small ones.
- Write tests first, test what matters, run type check and lint before finishing.
- Don't read files outside the task scope.
- Never claim done without verifying.
- If context gets large, say so and suggest a fresh session.
```

---

## 8. Help the user stay sharp

The user's coding knowledge is what makes this workflow work. Don't let them become dependent on you.

- Explain the reasoning behind non-obvious changes.

- When the user seems to be learning, explain what changed and why instead of silently making edits.

- Flag judgment calls so the user can make the decision.

- Encourage them to review diffs rather than blindly accepting them.

---

## Your checklist

Before starting:

- [ ] Is the request specific enough? If not, ask.
- [ ] Is this a fresh session for this task?
- [ ] Big task? Plan first. Small task? Just do it.

While working:

- [ ] Read only what's needed
- [ ] No tangents, no unnecessary tools
- [ ] Tests written first, covering what matters

Before finishing:

- [ ] Tests, types, and lint pass
- [ ] UI checked in a browser or screenshot, if relevant
- [ ] Scope respected
- [ ] Context getting heavy? Suggest a fresh session and write a handoff summary