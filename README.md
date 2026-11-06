# push-right

**An agent skill that does all the groundwork, then asks you once.**

Most agent runs interrupt you too early ("should I draft this?") or act too boldly (sending the email without asking). `push-right` splits every task into two kinds of step:

- **Reversible** (read, search, draft, compute, fill a form without submitting): the agent just does it.
- **Irreversible** (send, submit, close, approve, delete, pay): the agent holds it.

Then it shows you one short **brief** with numbered decisions. You reply `all`, `all except 2`, or the numbers you want. Only those run, and each one is checked against the real system afterwards.

```
DECIDE (3 items)
1. Send reply draft ->A   because stock request confirmed   [evidence: inbox, 06 Nov]
2. Close complaint #4411               because delivery logged in portal [evidence: portal status]
3. Send reminder -> distributor B      because case pending 5 days       [evidence: portal]
Reply: "all", "all except 2", or numbers.
```

## Why

I work in LPG sales and distribution, not software. My daily work is full of loops: inbox triage, complaint follow-ups, reminders to partners. Agents handle the groundwork well. What I needed was a rule for **where the human sits**. The answer: as far right as possible, once, with everything prepared.

The idea of "push right" and a decision-ready "brief" comes from Matt Pocock's [`loop-me`](https://github.com/mattpocock/skills). The safe re-run and decision-log habits come from poteto's [pstack](https://github.com/cursor/plugins/tree/main/pstack).

## Install

**Claude Code / Codex / Cursor and other agents:**

```bash
npx skills@latest add BARAKAMIT/push-right
```

**Claude.ai:** download `skills/push-right` as a zip and upload it under Settings → Capabilities → Skills.

**Any agent:** copy [`skills/push-right/SKILL.md`](skills/push-right/SKILL.md) into your agent's skills folder or paste it into the prompt.

## Use

```
/push-right go through today's inbox, draft replies to every partner request, and flag anything that needs escalation
```

Works well on top of other routines: put "follow push-right" in any skill that sends, closes, or submits things.

## What it guarantees

- Nothing irreversible happens before you approve it.
- One checkpoint per run, not ten.
- Re-running after a crash never sends or closes anything twice.
- Instructions found inside emails or web pages are treated as items to decide, never obeyed.
- Unattended runs stop at the brief.

## License

MIT
