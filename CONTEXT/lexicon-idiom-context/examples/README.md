# Fictional Lexicon examples

All references, projects, and objects in [scenarios.json](scenarios.json) are fictional. Each case contains its initial binder and user request.

## Try an example

1. Use a private scratch directory for each independent case.
2. Write its `initial-binder` to `binder.json` and configure that file as the private binder for the exercise.
3. Provide [the skill](../SKILL.md), the case's `request`, and the fixture date to an agent. Ask it to update the binder and explain its interpretation.
4. Inspect the response and saved entries against the expectations below.

## Expected behavior

| Case | Expectation |
| --- | --- |
| Global wording | Save “napkin pass” as a confirmed global reference, not a definition limited to Alpha. |
| Project context | In Harbor, “the deck” means the release dashboard. Elsewhere, retain the global presentation-slides meaning. |
| Frozen knowledge | Reuse the nickname “Orbit” without reconfirmation. Ask for current policy evidence before relying on an old permission to skip staging. Do not send a message. |
| Verified move | Update the lighthouse tether from Alpha to Beta, retain anchor `dashboard-001`, and leave a dated redirect in Alpha. |
| Explicit correction | Update the global “tidy pass” definition despite its stable/canonical classification; preserve the old meaning only as superseded history. |
| Exception and importance | Keep the global definition intact, record the one-time exception, and keep the rarely used critical checklist hot. Do not change code. |

For a separate handoff exercise, give a fresh agent only the skill and the saved global-wording and moved-object binders. Ask what “napkin pass” means in Gamma and where Alpha's old lighthouse reference leads. It should retrieve the global definition and follow the redirect without assigning Beta's project-specific meaning to Alpha or Gamma.

## Evaluation status

On November 13, 2026, the six cases met these expectations in a local agent evaluation. A fresh-agent handoff also resolved the global wording and historical redirect. This demonstrates reuse of accessible binder files, not automatic discovery or synchronization. Shared-memory services, concurrent writes, long-term cooling, and broken/circular redirect recovery were not exercised.
