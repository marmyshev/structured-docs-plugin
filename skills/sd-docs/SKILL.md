---
name: sd-docs
description: Use when asked to structure, reorganize, extract or migrate project documentation by levels of abstraction (goals, business rules, requirements, UI, technical decisions), to move legacy rule files into docs, or to record a user's decisions as documentation rules. Works level by level with the user, asking questions and never assuming.
---

# Structure documentation by level of abstraction

Process for turning scattered docs, rule files and code into consistent, concise documentation. Project-specific content never belongs in this skill.

A level is complete when its authorized items are recorded and indexed, their links resolve, and open decisions and implementation discrepancies are visible to the user.

## 1. Agree on the levels first

Each level answers one kind of question; higher levels constrain lower ones (a lower level that contradicts a higher one is wrong). Default set:

1. Goals: why the project exists, how success is measured.
2. Business rules, use cases and scenarios.
3. Technical requirements that apply everywhere.
4. UI behavior of pages and components.
5. Technical decisions: infrastructure, framework, program level.

Confirm the set, and the folder for each level, with the user. A folder name nobody specified is a decision: state it and let the user change it.

## 2. Work one level at a time

- Analyze and review one level, then present the draft, proposed file paths, and consequential choices together. Confirm new or changed decisions before recording them as rules. Publish authorized items and verify them before starting the next level.
- Ask instead of assuming. Give a suggested answer with each question so the user can confirm quickly.
- Keep undecided points in an open-questions file in the docs, not only in chat.

## 3. Ground each level in evidence

- Inspect the sources relevant to the level and identify any missing evidence that could change a conclusion.
- Use approved decisions as the authority for intended behavior and code, tests, or observed behavior as evidence of implementation. Record conflicts with approved rules as implementation discrepancies. Keep unclear decisions open.
- When evidence spans multiple domains and the host supports delegation, use parallel read-only agents to gather candidate rules and source references. Review the combined results before publishing.
- Check early that the tools you depend on (issue tracker, remote host) are reachable.

### Review the draft before publishing

For batches that add or change rules, check that each item belongs at the right level, agrees with approved higher-level rules, and cites evidence for its implementation claims. Resolve contradictions that the evidence or an approved decision settles. Bring unresolved choices that affect the outcome to the user.

When a second review could materially change the draft and `ce-doc-review` is available, invoke it through the active harness in non-interactive mode. Pass a readable temporary Markdown draft for the batch with stable item IDs, approved decisions, source references, and destination paths. Limit review edits to that draft. Inspect its changes and reconcile findings with the evidence and approval scope before presenting the batch.

Continue the built-in workflow if the optional review is skipped, unavailable, or incomplete. Mention incomplete coverage when it affects what the user can verify. For edits that preserve the rules' meaning, use the mechanical checks.

## 4. Separate decision from implementation

Every rule has two independent fields:

- **Decision:** decided or open. Owned by the user.
- **Implementation:** implemented, partial, broken or missing. Derived from the code.

Problems that are not rules go to a known-discrepancies file.

## 5. One item per file

- One file per rule, use case and UI scenario, each kind in its own folder.
- Each folder has an index; files link to related files and never copy their text.
- Write the policy in the top-level docs index so it outlasts the conversation.
- Mark statements that are unverified.

## 6. Re-verify when the ground moves

After a rewrite, migration or rebase, re-check the claims about current behavior before restructuring; the user's decisions stay. Make a backup branch before rewriting history, and use the smallest reversible Git operation.

## 7. Make the policies enforceable

Put these in the agent instruction file (for example `CLAUDE.md`) and in the docs index:

- Record every user decision as a rule on the matching level, concise but precise, and ask the user to review it.
- If a request contradicts an existing rule, propose a change to the rule and wait for the decision.
- Changes with high cost of error (such as data schema) need human confirmation before being applied.

Keep the instruction file short and point to the docs for detail.

## 8. Handle changed decisions as rule changes

Update the rule file, its index entry, every link to it, and related use cases and open questions. Rename files whose title no longer fits.

## 9. Verify mechanically

- Run a link check over all documents after each batch of edits.
- Search for stale wording after a decision change.
- Stage and commit named paths only.
- If a sandbox or permission blocks a push or PR, report it with the exact commands for the user; do not bypass it.
