# Contributing to designgov.md

Thank you for your interest in contributing. `designgov.md` is an open standard — its value grows with the diversity of people and organizations who shape it.

This document explains how to contribute effectively.

---

## Who should contribute

`designgov.md` was built to address a problem that shows up across industries, company sizes, and organizational structures. We want contributions from:

- **Design ops and design systems practitioners** who govern brand consistency at scale
- **Designers and design leads** who have fought the battle between design intent and engineering output
- **Product and engineering leaders** who have inherited the consequences of brand drift after acquisitions, reorgs, or leadership changes
- **Accessibility specialists** who have seen WCAG debt accumulate because enforcement happened too late in the process
- **Developers** who use AI coding agents and want better governance tooling in their workflow
- **Anyone who has lived through** a merger, acquisition, spin-off, rebrand, or market pivot and watched the design language fragment in real time

You do not need to be a designer to contribute. Some of the most valuable contributions will come from engineers who understand how AI agents consume context files, and from operations people who understand how governance frameworks break down at scale.

---

## Ways to contribute

### 1. Add an example

Examples are the most valuable contribution to the repository. A filled `designgov.md` for a real or fictional organization teaches the spec better than any documentation.

**Examples we particularly want:**

- **SaaS companies** that have grown through acquisition or serve multiple market segments
- **Healthcare** — patient portals, clinical tools, and consumer health products with HIPAA and Section 508 implications
- **Financial services** — multi-brand retail banking, wealth management, and fintech with compliance constraints
- **Government and civic tech** — products subject to WCAG 2.1 AA legal requirements and multi-agency brand governance
- **Media and publishing** — parent brands managing acquired titles, platforms, and audiences with different expectations
- **Enterprise software** — products serving both IT administrators and end users, often with radically different design languages
- **Consumer + enterprise dual-track** — companies that run a consumer product and an enterprise product under the same brand umbrella
- **Post-acquisition portfolios** — any organization managing brands at different levels of alignment after M&A activity

**To add an example:**

1. Fork the repository
2. Create a folder at `examples/[organization-name]/`
3. Copy [`SPEC.md`](./SPEC.md) into the folder and rename it `designgov.md`
4. Fill out every section — the more complete the better
5. Add a brief `README.md` in the folder explaining the fictional or real organization context
6. Open a pull request with the title `example: [organization name] — [industry]`

**Guidelines for examples:**

- Fictional companies are encouraged — you don't need a real company's permission
- If using a real company as inspiration, change names, colors, and identifiable details
- Fill out all eight sections — partial examples are harder to learn from
- The hybrid brand architecture section (section 6) is the most differentiated part of the spec — try to use it meaningfully, not just as a placeholder
- Include at least three entries in the behavioral NEVER list based on real patterns you've observed
- Include at least two entries in the Tier 3 accessibility prohibited patterns list

---

### 2. Improve the specification

The spec is at v0.1. There are gaps, ambiguities, and governance problems it doesn't yet address.

**Open an issue if:**

- You encounter a governance scenario the current spec structure can't represent
- A section is ambiguous in ways that would cause inconsistent implementations
- The AI coding agent instructions could be more precise or more useful
- A field or section is missing that would be valuable across multiple industries
- The tiered accessibility model needs refinement for a specific context

**Submit a pull request if:**

- You have a clear improvement to existing spec language
- You want to add a new field or section with a concrete rationale
- You want to fix a factual error in the accessibility guidance

For significant structural changes to the spec, open an issue first to discuss before investing time in a PR.

---

### 3. Deepen or add vertical extensions

Section 4.5 of the spec contains domain-specific governance requirements for four industries: Education, Healthcare, Financial services, and Government. These are starting points — each vertical has more depth than a single section can capture.

**Ways to contribute to existing verticals:**

**Education (4.5a)**
- Assistive technology testing protocols for institutional environments (JAWS + older browsers, switch access in classroom settings)
- LMS-specific governance patterns (Canvas, Blackboard, Moodle)
- Assessment accessibility edge cases beyond the core checklist

**Healthcare (4.5b)**
- HIPAA-influenced UI patterns — what information can appear where, audit trail implications for UI decisions
- Clinical vs. patient-facing governance — the same organization often needs radically different rules for each
- Emergency and critical-information UI patterns that override standard design conventions
- EHR integration governance — when your UI surfaces data from external clinical systems

**Financial services (4.5c)**
- Fraud and security UI patterns that must be consistent across products
- Accessibility requirements for aging and low-literacy user populations
- Mobile banking governance — native app vs. web parity requirements

**Government and civic tech (4.5d)**
- Multi-language and translation governance — which content must be translated, what the fallback behavior is
- Low-bandwidth and legacy device testing protocols
- Procurement compliance documentation patterns

**Verticals we want to add:**

**Enterprise software**
- Admin vs. end-user interface governance within the same product
- Role-based UI complexity patterns — what a power user sees vs. a casual user
- Data density and information architecture for tool-dense environments
- Multi-tenant governance — when the same UI serves customers with different brand requirements

**Media and publishing**
- Parent brands managing acquired titles with different audiences
- Editorial vs. product UI governance within the same organization
- Syndication and licensing governance for UI components

To propose a new vertical or deepen an existing one, open an issue with the title `vertical: [industry]` and describe the governance requirements specific to that domain.

---

### 4. Build tooling

The spec is a markdown file. Tooling makes it actionable. We welcome:

**Validators**
- A linter that checks a `designgov.md` file for structural completeness
- A CI integration that flags missing required sections before merge
- A contrast checker that validates color combinations declared in section 1.1

**Generators**
- A CLI or web tool that asks questions and outputs a populated `designgov.md`
- A Figma plugin that extracts tokens and pre-populates section 1
- An integration with Google's `DESIGN.md` toolchain that imports visual tokens into section 1 and prompts for the governance layers

**AI agent integrations**
- Example `claude.md` snippets that instruct agents to read and enforce `designgov.md`
- BMAD workflow configurations that incorporate `designgov.md` into the build process
- Cursor rules and Copilot instruction patterns for `designgov.md` enforcement

**For tooling contributions:**
- Open an issue first describing what you want to build
- Tooling lives in the `tools/` directory
- Include a README explaining installation, usage, and any dependencies
- MIT license required for all tooling contributions

---

### 5. Translate the specification

Design governance is a global problem. If you want to translate the spec into another language:

- Create a folder at `translations/[language-code]/`
- Translate `SPEC.md` — examples can stay in English or be translated separately
- Open a PR with the title `translation: [language name]`
- You will be listed as the translation maintainer

---

## Pull request guidelines

**Before opening a PR:**

- Open an issue first for significant changes — it saves everyone time
- Check existing PRs to avoid duplicate work
- Read the spec carefully so your contribution is consistent with existing structure and tone

**PR titles:**
- `example: [org name] — [industry]` for new examples
- `spec: [brief description]` for spec changes
- `fix: [brief description]` for corrections
- `tooling: [tool name]` for new tools
- `vertical: [industry]` for vertical extensions
- `translation: [language]` for translations
- `docs: [brief description]` for documentation improvements

**PR description should include:**
- What problem this contribution addresses
- What section(s) of the spec it touches or extends
- For examples: a 2–3 sentence description of the fictional or real organization context
- For spec changes: the rationale and any tradeoffs considered

---

## Code of conduct

`designgov.md` is a professional community. Contributions and discussions should be:

- **Specific** — concrete governance problems and concrete solutions, not abstract opinions
- **Constructive** — critique the spec, not the people who wrote it
- **Inclusive** — governance problems look different at different company sizes, industries, and geographies; all perspectives are valuable
- **Honest about uncertainty** — design governance is a young discipline; we don't have all the answers and that's fine

---

## Recognition

Significant contributors will be acknowledged in the repository README. Example contributors will be credited in their example's folder README.

If you build tooling that gets adopted by the community, you'll be listed as a maintainer of that tool.

---

## Questions

Open a GitHub Discussion if you have questions about contributing that aren't answered here.

---

*designgov.md is maintained by [Ken Griffin](https://linkedin.com/in/kengriffin-designops) and the community.*  
*MIT License — free to use, adapt, and build on.*
