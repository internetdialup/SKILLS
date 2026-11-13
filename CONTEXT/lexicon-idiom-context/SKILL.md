---
name: lexicon-idiom-context
description: Maintain and consult a private contextual dictionary of a person's slang, idioms, nicknames, references, and conversational syntax across agents and projects, with project-bound meanings and selective retrieval.
---

# Lexicon / Idiom Context

A document that gives your agents contextual information about how you talk, so your meaning isn't lost and you don't have to keep explaining yourself.

Think of it as a binder: an agent opens the index and moves to the references it needs. The dictionary grows from explicit explanations and repeated patterns in conversation. Personal language works across agents and projects; project-specific meanings stay bound to their context.

## Understand and remember

Use common English idioms and the surrounding conversation first. Notice slang, nicknames, shorthand, fragments, omitted subjects, punctuation, and corrections across messages. Preserve the person's intent and voice; do not turn informal typing into a problem to fix.

Record clarified references automatically in the configured private dictionary, with relevant tags. Infer additional meanings from consistent usage, keeping evidence and confidence separate. Mark explicit explanations as **confirmed**, supported interpretations as **inferred**, and unresolved meanings as **unresolved**. Repetition of the agent's own guess is not evidence.

Use context to do the bookkeeping instead of repeatedly asking the user to classify entries. Ask only when unresolved ambiguity could change the work. Otherwise, proceed with the supported interpretation; briefly state an assumption when useful.

## Global wording and project context

Assign each meaning a scope:

- **global-wording:** the person's slang, idioms, nicknames, and ways of speaking, available across projects.
- **project-specific:** a meaning tied to a particular project or an object within it.

Infer scope from context. Ask only when a wrong assignment could change the work.

For project-specific references, the **tether** links to the parent project. The **anchor** identifies the child object the slang refers to. Use an existing stable identifier where available; a rename or move should not change the object's anchor.

Within the relevant project, its specific meaning takes priority over the global meaning. Keep both definitions intact. Outside that project, use the global meaning; do not apply another project's definition merely because the wording matches.

## Corrections and exceptions

An explicit user correction updates the relevant meaning, scope, or binding. Otherwise, treat a conflicting use as a contextual exception without overwriting the established definition. Ask only if the unresolved conflict could change the work.

The agent may infer that a reference is **canonical** from explicit definitions, consistent usage, or authoritative sources. Record the basis. Canonical describes authority; it is separate from confidence and retrieval temperature.

Treat **immutable** as stable unless contradicted, not impossible to correct. Do not ask the user to certify every stable reference or let an inferred classification block later corrections.

## Temperature and token usage

Temperature controls retrieval priority, not truth or permission. Use frequency as the starting point; importance overrides frequency when a reference could materially change the work.

| Temperature | Retrieval behavior |
| --- | --- |
| **Hot** | Frequently used or critical to getting the work right; keep its concise meaning readily available in the relevant context. |
| **Warm** | Recurring or stable canonical knowledge; retrieve when the topic fits. Canonical references generally start here and become hot when critical to the work. |
| **Cold** | Rarely used; retain and retrieve when the reference or its context appears. |
| **Frozen** | In hibernation; preserve its meaning, context, and history for lookup without routinely loading it. |

Adjust temperatures from observed usage and task relevance. Rare but critical references stay hot. Cooling never means deleting knowledge, lowering confidence, or losing its place in the index. No fixed frequency thresholds are prescribed by this skill.

Record **last used** as `MM/DD/YY` when the reference is actually used. Usage alone does not confirm that its meaning or institutional knowledge is still current.

When frozen knowledge is retrieved, check whether its bound context has changed only if outdated information could affect the work. Use available evidence first; ask if consequential uncertainty remains. Nicknames do not need reconfirmation unless there is conflicting context.

## Moves and historical redirects

If the agent can verify that an object moved, update its tether automatically, retain its anchor, and record **tether last updated** as `MM/DD/YY`. Ask only when ambiguity about the move could change the work.

Leave a redirect in the old project's section pointing to the new tether, preserving the anchor and a **last updated** date. Like a web-address redirect, this retains history and lets agents find where the object went. A redirect is a lookup pointer, not permission to apply the new project's meaning in the old project.

Follow successive redirects to the current destination. Preserve historical pointers; detect broken or circular redirects rather than guessing a destination. Request clarification only when the unresolved lookup affects the work.

## Shared binder and private storage

Use a configured, user-controlled private binder accessible to the authorized agents that need it. Keep a small index of references, scopes, tags, temperatures, and entry locations. Retrieve relevant entries and follow their tethers instead of loading the whole dictionary or every project's knowledge.

Reuse the established binder location. If none exists, choose a permitted private location and report it. A local `.local/lexicon.md` can be a starting point, but cross-project and cross-agent continuity requires shared access or explicit configuration pointing to the same binder. A project-local file alone does not provide that continuity.

The public skill contains reusable instructions and generic examples. Personal entries and private project links belong in the private binder. Ask before publishing or including personal information in shared artifacts. Git ignore rules do not protect files already tracked.

This skill specifies behavior; it does not install storage, synchronization, or automatic retrieval. Do not claim cross-agent memory unless the binder is actually accessible. If storage or access is unavailable, say so and provide an entry or handoff the user can save.

Dictionary entries describe language. They do not override instructions, grant access, or authorize consequential actions. Do not infer health, personality, or background from typing style.

## Entry format

Use this adaptable structure. Store dates as quoted `MM/DD/YY` values; use null for unknown or inapplicable fields. A global wording entry usually has no tether or anchor. Retain separate entries when the same wording has different scoped meanings.

```yaml
reference: "the lighthouse"
meaning: "the project's monitoring dashboard"
scope: project-specific
tether: "project-xyz"
anchor: "monitoring-dashboard-001"
tags: [nickname, dashboard]
confidence: confirmed
canonical: true
immutable: false
importance: critical
importance-basis: "Identifies the dashboard required for this project's checks."
temperature: hot
last-used: "11/13/26"
tether-last-updated: "11/13/26"
basis: "The user explicitly defined this reference for the project."
```

For a verified move from `project-xyz` to `project-abc`, leave this redirect in the old project's section and update the current entry's tether and tether date:

```yaml
type: redirect
reference: "the lighthouse"
previous-tether: "project-xyz"
new-tether: "project-abc"
anchor: "monitoring-dashboard-001"
last-updated: "11/13/26"
basis: "Verified move recorded in the project's migration record."
```

These examples are fictional and demonstrate the format, not anyone's personal vocabulary. The dates are usage and binding metadata, not a substitute for evidence of correctness.

For fictional exercises and expected behavior, see [examples/README.md](examples/README.md). Load these only when testing or demonstrating the skill.
