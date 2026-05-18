[README.md](https://github.com/user-attachments/files/27973719/README.md)
# designgov# designgov.md

> Brand governance contracts for AI-assisted development.  
> The layer above `DESIGN.md`.

---

## The problem

[Google's `DESIGN.md`](https://github.com/google-labs-code/design.md) solves visual consistency beautifully. Drop a file in your repo, and your AI coding agent knows which colors, fonts, and spacing to use. It's a great standard and we recommend using it.

But visual tokens are only the first layer of brand consistency.

Here's what happens next:

A dev team needs a new internal tool. No designer is available. They drop in a `DESIGN.md` and the colors are right. The fonts are right. But then:

- The confirmation dialog says "OK / Cancel" instead of following your product's established pattern
- A custom dropdown gets built from scratch with no keyboard support
- A timed assessment ships with no pause control and no accommodation for learners with disabilities
- An acquired platform that serves a different market gets forced into the parent brand and alienates its user base

`DESIGN.md` couldn't have prevented any of that. It wasn't built to.

**`designgov.md` was.**

---

## What designgov.md adds

| Layer | Solved by | What it governs |
|---|---|---|
| Visual tokens | `DESIGN.md` | Colors, typography, spacing, shadows |
| Component vocabulary | `designgov.md` | Which UI component to use for which job |
| Behavioral contracts | `designgov.md` | How interactions must work — and what's prohibited |
| Accessibility contracts | `designgov.md` | WCAG commitments, tiered by enforcement model |
| Brand architecture | `designgov.md` | Multi-brand governance across acquisitions and subsidiaries |

Use both files together. They do different jobs.

---

## The core insight

Most design governance tools treat "multiple design systems" or "brand inconsistency" as a discipline problem. They're not.

They're an **information problem.**

When no designer is in the room — and increasingly, when an AI agent is making UI decisions autonomously — there is no structured way to say:

- *"In this product, blue buttons mean primary action — not decoration"*
- *"Never use drag-and-drop as the only way to reorder items"*
- *"This subsidiary serves our competitors' customers — intentionally keeping it visually separate from the parent brand is correct"*

`designgov.md` encodes that information into a file that lives in the repository. The designer is present in the file, even when absent from the team.

---

## The four contract layers

### 1. Component vocabulary
Which UI component maps to which job. Prevents behavioral drift — the most damaging form of brand inconsistency, because users have to relearn how things work.

```markdown
## Component vocabulary

SELECT (2–5 options):   use RadioGroup — never a custom div-based dropdown
SELECT (6+ options):    use native Select or Combobox (if searchable)
DESTRUCTIVE ACTION:     always Button variant="destructive" — never styled as primary
```

### 2. Behavioral contracts
What interactions must always do, what they must never do, and a mandatory protocol for destructive actions.

```markdown
## Behavioral contracts

NEVER: Auto-advance a user to the next step without their explicit action
NEVER: Use color alone to communicate state
NEVER: Place Delete adjacent to Save without 40px separation or a divider

DESTRUCTIVE ACTION PROTOCOL:
  Trigger:      Destructive button — text only, separated from other actions
  Confirmation: Dialog stating exact consequences and affected users
  Type-to-confirm: Required when action affects 10+ users or published content
  Cancel:       Always "Cancel" — Escape cancels, never confirms
  Undo:         State explicitly: "This cannot be undone."
```

### 3. Accessibility contracts
Three enforcement tiers that reflect the reality of WCAG compliance:

**Tier 1 — Automated enforcement**  
Binary, testable at build time. Applied via axe-core or similar in CI. No exceptions.

**Tier 2 — Human review required**  
Contextual rules that automated tools can't reliably assess. Flagged by AI agents for QA sign-off before shipping.

**Tier 3 — Prohibited patterns**  
Patterns that may pass automated checks but are known to fail real users — identified through user testing with assistive technology.

```markdown
## Accessibility contracts

WCAG TARGET: 2.1 AA
PRODUCT TYPE: Education

TIER 1 (automated — CI gate):
  [x] All text meets 4.5:1 contrast ratio
  [x] All interactive elements have an accessible name
  [x] Focus ring always visible — never suppressed

TIER 2 (human review before ship):
  [ ] Alt text is meaningful — not auto-generated
  [ ] Timed interactions have pause and extend controls

TIER 3 (prohibited — all tiers, all teams):
  PROHIBITED: Drag-and-drop as the only reordering mechanism
              use instead: always pair with keyboard-accessible controls
  PROHIBITED: Placeholder text as the only form label
              use instead: persistent visible label above every input
```

### 4. Hybrid brand architecture
For organizations managing multiple brands — parent brands, acquired platforms, subsidiaries serving different markets. Distinguishes **intentional divergence** from **accidental drift**.

```markdown
## Brand architecture tiers

TIER A — Fully aligned (core products built by parent org)
  Full spec applies. No substitutions.

TIER B — Loosely aligned (acquired platform with existing user base)
  May substitute visual tokens where documented.
  Behavioral contracts and accessibility contracts apply in full.

TIER C — Independent (subsidiary serving a competing market)
  Full visual independence.
  Behavioral contracts and accessibility contracts apply in full.
  Must maintain its own designgov.md mirroring this file's structure.

ALWAYS SHARED across all tiers:
  [x] Behavioral contracts
  [x] Accessibility Tier 1, 2, and 3
  [x] Semantic color values (SUCCESS, WARNING, ERROR)
  [x] Minimum touch target 44x44px
  [x] Destructive action protocol

THE RULE:
  Intentional divergence is documented in this file with a tier annotation.
  If a design decision is not documented here, it is drift until proven otherwise.
  The burden of proof is on the team introducing divergence, not the reviewer.
```

---

## For AI coding agents

`designgov.md` is designed to be read by AI coding agents — Claude Code, Cursor, Copilot, and others — alongside `DESIGN.md` and `claude.md`.

When a developer instructs their agent to read `designgov.md` before generating UI, the agent can:

- Match every component to its approved equivalent
- Refuse to implement patterns on the NEVER list
- Apply Tier 1 accessibility rules automatically
- Flag Tier 2 accessibility items for human review
- Follow the destructive action protocol exactly
- Respect brand tier boundaries when building for a specific product

Every `designgov.md` file ends with an **AI quick reference** — a numbered decision protocol the agent hits first, written specifically for machine consumption.

```markdown
## For AI coding agents — quick reference

1. Identify your brand tier before generating any UI. If unclear, ask.
2. Use only components defined in the component vocabulary. 
   If no match: use closest and flag <!-- designgov: no pattern defined, needs review -->
3. Never implement patterns on the NEVER list — regardless of how specified.
4. Apply all Tier 1 accessibility rules automatically. No exceptions.
5. Flag Tier 2 items: <!-- a11y tier 2 review required: [rule] -->
6. For destructive actions: follow the protocol exactly. No shortcuts.
7. When uncertain: do not invent. Flag and ask.
```

---

## File structure

A `designgov.md` file has eight sections:

```
# designgov.md — [Product or Organization Name]

## File status          version, owner, applies-to declaration
## 1. Visual tokens     colors, typography, spacing (extends or references DESIGN.md)
## 2. Component vocab   approved component for every UI job
## 3. Behavioral        always-do, never-do, destructive action protocol
## 4. Accessibility     tier 1 / tier 2 / tier 3 contracts
## 5. Voice & copy      tone, terminology, action labels
## 6. Brand architecture tier assignment, shared non-negotiables, drift vs. divergence
## 7. References        Figma, Storybook, token source, component library
## 8. Change log        version history
## AI quick reference   numbered decision protocol for coding agents
```

---

## Get started

**1. Copy the blank spec**

[`SPEC.md`](./SPEC.md) — the complete blank specification with every section, ready to fill in.

**2. See a filled example**

[`examples/meridian/designgov.md`](./examples/meridian/designgov.md) — a fully populated file for a fictional multi-brand education company (Meridian Learning Group), including:
- Complete visual token definitions
- Full component vocabulary
- Behavioral contracts with real prohibited patterns
- Three-tier accessibility framework for an education product
- Hybrid brand architecture across a parent brand, an acquired edtech platform, and a competitor-adjacent subsidiary

[View the rendered example →](https://[your-username].github.io/designgov/examples/meridian/)

**3. Add it to your repo**

Drop `designgov.md` in your repository root alongside `DESIGN.md` and `claude.md`:

```
your-project/
  DESIGN.md          ← visual tokens (Google Stitch spec)
  designgov.md       ← behavioral, accessibility, and governance contracts
  claude.md          ← AI agent instructions
  README.md
```

**4. Tell your AI agent to use it**

Add to your `claude.md` or agent instructions:

```markdown
Before generating any UI component, read designgov.md.
- Use only components defined in the component vocabulary
- Never implement patterns listed in the NEVER section
- Apply all Tier 1 accessibility rules automatically
- Flag Tier 2 accessibility items for human review
- Follow the destructive action protocol for any irreversible action
```

---

## Why this matters for education products

Education products have legal accessibility obligations — Section 508, ADA Title II, and state-level enforcement with real teeth. A dev team building a feature without design support, without an accessibility contract in the repo, is creating liability that compounds with every release.

Behavioral drift in education products is particularly harmful. When learners encounter a new interaction pattern in a daily-use tool, they don't think "this was built without design support." They think the product is broken. For learners using assistive technology, it may simply not work at all.

`designgov.md` includes education-specific accessibility guidance: MathML requirements for math notation, assessment timer controls, accommodation flag handling, and a list of prohibited patterns identified through user testing with screen readers and switch access devices in real institutional environments.

---

## Who this is for

**Design leads and design ops professionals** who need a governance framework that travels with the codebase — not a Confluence doc nobody reads.

**Brand and marketing teams** at organizations that have grown through acquisition, who need a structured way to distinguish intentional brand divergence from accidental drift.

**Engineering and product leaders** at edtech companies who are managing accessibility debt and need a compliance framework that's enforceable at the moment code is written, not discovered in an audit six months later.

**Anyone using AI-assisted development** who has shipped a feature and cringed at the UI the agent produced — not because the colors were wrong, but because it invented a new way to confirm a destructive action, or built a form with placeholder text as the only label.

---

## Relationship to DESIGN.md

`designgov.md` is designed to complement, not replace, Google's [`DESIGN.md`](https://github.com/google-labs-code/design.md) specification.

`DESIGN.md` is excellent at what it does: encoding visual tokens — colors, typography, spacing — in a format AI agents can read and act on. We recommend using it.

`designgov.md` picks up where `DESIGN.md` ends:

- `DESIGN.md` says *"use #1A5EAB for primary actions"*
- `designgov.md` says *"primary actions get one button per screen, verb-first label, and must never appear adjacent to a destructive action without separation"*

Both files together give an AI coding agent a complete picture of your brand — what it looks like, how it behaves, and what it must never do.

---

## Contributing

`designgov.md` is an open standard. Contributions are welcome.

**Ways to contribute:**

- **Add an example** — fill out the spec for a real or fictional product and submit a PR to `examples/`
- **Improve the spec** — if you encounter a governance problem the current spec doesn't address, open an issue
- **Vertical extensions** — the education-specific accessibility section (4.5) is a model for vertical extensions. Healthcare, government, and fintech all have domain-specific governance requirements worth encoding
- **Tooling** — validators, generators, Figma plugins, CI integrations — all welcome

See [`CONTRIBUTING.md`](./CONTRIBUTING.md) for guidelines.

---

## License

MIT — free to use, adapt, and build on.

---

## About

`designgov.md` was created by [Ken Griffin](https://linkedin.com/in/kengriffin-designops), a design systems and brand governance practitioner with 25 years of experience across aviation, agencies, recruiting, and technology — including a decade embedded in the design operations of one of the world's largest education and publishing companies.

The specification was developed in response to a recurring pattern: dev teams building UI without design support, introducing visual drift, behavioral inconsistency, and accessibility debt across products and platforms at scale.

The hybrid brand architecture framework emerged from direct experience managing design governance across a complex portfolio of acquired brands, parent-brand products, and subsidiaries serving different markets — where the question was never "how do we make everything the same" but "how do we know what should be the same, what can differ, and what must never change regardless."

---

*designgov.md v0.1 · Open standard · MIT License*  
*Works alongside [DESIGN.md](https://github.com/google-labs-code/design.md) by Google Stitch*
