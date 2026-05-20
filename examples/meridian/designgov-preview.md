# designgov.md — Meridian Learning Group
### Parent Brand Specification with Hybrid Architecture Guidance

> This file is the authoritative brand and design contract for all Meridian Learning Group products.  
> It includes guidance for subsidiary brands at each level of brand attachment.  
> Maintained by the Meridian Design Systems team.

---

> **📄 This is a preview.** Sections 1 and 2 are shown in full.  
> Sections 3–8 (behavioral contracts, accessibility contracts, voice and copy,  
> hybrid brand architecture, references, and change log) are available in the  
> complete example pack.  
>  
> **[Get the complete Meridian example pack →](https://7511476758677.gumroad.com/l/ofiihn)**  
> Includes the full designgov.md, the rendered HTML documentation viewer, and an adaptation guide.

---

## How to read this file

Throughout this document you will see annotation blocks like this:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ TIER A — FULLY ALIGNED                                                      │
│ Applies to: Meridian.com, Meridian Learn, Meridian Press                    │
│ [guidance]                                                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER B — LOOSELY ALIGNED                                                    │
│ Applies to: Pathwright (acquired edtech platform)                           │
│ [guidance]                                                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER C — INDEPENDENT                                                        │
│ Applies to: Vantage Professional (corporate certification division)         │
│ [guidance]                                                                  │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Tier A** products are fully brand-aligned and must implement this spec completely.

**Tier B** products are acquired or semi-autonomous brands with their own user base and visual identity. They share the structural and behavioral layer of this spec but may substitute their own visual tokens where documented.

**Tier C** products serve markets where visible Meridian branding would create commercial conflict. They are legally and operationally part of Meridian Learning Group but maintain independent brand identities. They must implement behavioral contracts and accessibility contracts in full. Visual tokens and component vocabulary are their own, but the structure of their designgov.md must mirror this file.

**Why this matters:** Brand drift is not always a failure of discipline. Sometimes it is an unintended consequence of acquisition, market positioning, or competitive reality. This file distinguishes between *accidental drift* (a problem to fix) and *intentional divergence* (a strategic decision to document). The tier system makes that distinction explicit and auditable.

---

## File status

```
Status:        [x] Active
Version:       1.2
Last updated:  2025-03-01
Owner:         Sarah Chen, VP Design Systems
Product:       Meridian Learning Group — Parent Brand
Applies to:    [x] All UI
```

---

## 1. Visual tokens

### 1.1 Color palette

```
PRIMARY ACTION:     hex: #1A5EAB   usage: Primary buttons, key links, active states
PRIMARY HOVER:      hex: #144D8C   usage: Hover and pressed state for primary elements
SECONDARY ACTION:   hex: #F0F5FB   usage: Secondary buttons, subtle CTAs
BACKGROUND:         hex: #FFFFFF   usage: Page/screen background
SURFACE:            hex: #F7F9FC   usage: Cards, panels, elevated containers
BORDER:             hex: #D1DBE8   usage: Dividers, input outlines, table borders
TEXT PRIMARY:       hex: #1A1F36   usage: Body text, headings, primary labels
TEXT SECONDARY:     hex: #5A6481   usage: Supporting text, captions, metadata
TEXT DISABLED:      hex: #A8B2C4   usage: Disabled state labels only
SUCCESS:            hex: #1A7F5A   usage: Confirmation messages, success states
WARNING:            hex: #B45309   usage: Cautionary states, non-critical alerts
ERROR:              hex: #C0392B   usage: Error messages, destructive action indicators
INFO:               hex: #1A5EAB   usage: Informational states
FOCUS RING:         hex: #F5A623   usage: Keyboard focus indicator — high contrast amber
```

**Color rules — always enforced:**

- Never use a color outside this palette without explicit approval
- Never use color as the only means of conveying information
- Never use ERROR color for anything except actual errors
- FOCUS RING must always be visible — never suppress or override it

**Prohibited color combinations:**

```
PROHIBITED:  #5A6481 on #FFFFFF at text sizes below 16px
             reason: fails WCAG AA — use TEXT PRIMARY instead

PROHIBITED:  #FFFFFF on #1A5EAB at sizes below 14px
             reason: marginal contrast at small sizes

PROHIBITED:  #F5A623 on #F7F9FC without 2px offset
             reason: insufficient focus visibility on light surfaces
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ TIER A — Meridian core products                                             │
│ Use this palette exactly. No substitutions.                                 │
│ Internal tools must also use this palette — not arbitrary CSS frameworks.   │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER B — Pathwright                                                         │
│ Pathwright retains its own primary palette (teal #007C91, white, dark navy).│
│ REQUIRED to adopt: FOCUS RING, SUCCESS, WARNING, ERROR, TEXT DISABLED.      │
│ These semantic colors must be consistent across the Meridian product family.│
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER C — Vantage Professional                                               │
│ Vantage maintains its own full palette (charcoal, gold, white).             │
│ REQUIRED to adopt: SUCCESS, WARNING, ERROR hex values only.                 │
│ All other color decisions are Vantage's own.                                │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 1.2 Typography

```
PRIMARY FONT:    Source Serif 4   usage: Editorial, marketing, reading content
UI FONT:         Inter            usage: All UI chrome — nav, forms, labels, buttons
MONOSPACE:       JetBrains Mono   usage: Code, identifiers, technical values only
FALLBACKS:       Georgia, serif / -apple-system, sans-serif / Courier New, monospace

NOTE: Never use Source Serif 4 for UI elements. Never use Inter for article body.

UI SCALE (Inter):
  H1:      32px   weight: 600   line-height: 1.2
  H2:      24px   weight: 600   line-height: 1.3
  H3:      20px   weight: 500   line-height: 1.4
  H4:      16px   weight: 600   line-height: 1.4
  Body:    16px   weight: 400   line-height: 1.6
  Small:   14px   weight: 400   line-height: 1.5   usage: Captions, metadata
  Label:   13px   weight: 500   line-height: 1.4   usage: Form labels, tags
  Code:    14px   weight: 400   line-height: 1.7   font: JetBrains Mono

EDITORIAL SCALE (Source Serif 4):
  Display: 48px   weight: 700   line-height: 1.1   usage: Hero headings only
  H1:      36px   weight: 600   line-height: 1.2
  Body:    18px   weight: 400   line-height: 1.7   usage: Article body, course descriptions
  Pull:    24px   weight: 300   line-height: 1.5   italic — pull quotes only
```

**Typography rules — always enforced:**

- Never set body text below 14px in any context including mobile
- Never use Source Serif 4 for buttons, labels, or navigation
- Never use ALL CAPS for strings longer than 4 words
- Never use italic outside pull quotes, citations, or editorial emphasis

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ TIER A  Both font families required. No system font substitutions.          │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER B  Pathwright uses DM Sans (approved Inter substitution).              │
│         Source Serif 4 required for Meridian-branded content within         │
│         Pathwright (e.g. Meridian Press titles, catalog descriptions).      │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER C  Full font independence. Vantage uses Neue Haas Grotesk + Tiempos.   │
│         14px minimum body size still applies.                               │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 1.3 Spacing system

Base unit: 8px. All values must be multiples of 8 (or 4 for tight contexts).

```
xs:    4px    icon-to-label gap, tight internal padding
sm:    8px    input internal padding, stacked label-to-input gap
md:    16px   button padding, card internal padding, form field spacing
lg:    24px   section separation within a page region
xl:    40px   major section breaks, card grid gaps
2xl:   64px   page-level vertical rhythm, hero padding
3xl:   96px   large editorial layouts only
```

Never use arbitrary pixel values. Never use negative margins to fix layout.

---

### 1.4 Border radius

```
NONE:   0px      data tables, code blocks, technical UI
SM:     4px      badges, tags, inline code
MD:     8px      inputs, buttons, small cards, dropdowns
LG:     12px     cards, panels, modals, dialogs
XL:     20px     feature cards, promotional modules — deliberate use only
FULL:   9999px   avatar circles, pill status indicators only
```

### 1.5 Elevation and shadow

```
FLAT:     none
RAISED:   0 1px 3px rgba(26,31,54,0.10), 0 1px 2px rgba(26,31,54,0.06)
OVERLAY:  0 10px 25px rgba(26,31,54,0.15), 0 4px 10px rgba(26,31,54,0.08)
FOCUS:    0 0 0 3px #F5A623
```

---

## 2. Component vocabulary

### 2.1 Navigation

```
PRIMARY NAV:     MDS TopNav — logo left, links center, account right
                 Never reorder. Never exceed 6 primary links.

SECONDARY NAV:   MDS SideNav (application contexts)
                 MDS TabBar (content section switching within same context)
                 Never use both simultaneously on the same screen.

BREADCRUMBS:     MDS Breadcrumb — use when 3+ hierarchy levels present

BACK NAV:        MDS BackLink — "Back to [specific place]", never just "Back"

TABS:            MDS TabBar — switching related views at same hierarchy level
                 Never for page/route navigation. Never more than 6 tabs desktop, 4 mobile.
```

### 2.2 Actions

```
PRIMARY:         MDS Button variant="primary" — one per screen region, verb-first label
SECONDARY:       MDS Button variant="secondary"
GHOST:           MDS Button variant="ghost" — low-emphasis competing actions
DESTRUCTIVE:     MDS Button variant="destructive" — always follow section 3.3 protocol
ICON-ONLY:       MDS IconButton — always requires aria-label + MDS Tooltip
LOADING:         MDS Button with loading prop — show after 200ms on all async actions
```

### 2.3 Forms and inputs

```
TEXT INPUT:      MDS Input
MULTILINE:       MDS Textarea
SELECT (2–5):    MDS RadioGroup or MDS Select (space-constrained)
SELECT (6+):     MDS Select or MDS Combobox (if searchable)
SEARCH:          MDS SearchInput (includes clear + search icon)
DATE:            MDS DatePicker
FILE:            MDS FileUpload (drag-and-drop always paired with click fallback)
CHECKBOX:        MDS Checkbox (multiple selection allowed)
RADIO:           MDS RadioGroup (single selection from defined set)
TOGGLE:          MDS Switch (immediate binary state change only)
SLIDER:          MDS RangeSlider (always show current value as visible text)
```

**Form rules — always enforced:**

- Every input: visible persistent label above the field — never placeholder-only
- Every input: reserved space below for error message — never shift layout on error
- Never disable submit as the only error communication — show inline errors
- Always validate on blur — never wait for submission to surface errors
- Never clear form on validation failure — always preserve user input

### 2.4 Feedback and status

```
SUCCESS TOAST:   MDS Toast variant="success"   auto-dismiss: 5000ms
ERROR TOAST:     MDS Toast variant="error"     never auto-dismiss
WARNING TOAST:   MDS Toast variant="warning"   auto-dismiss: 8000ms
INLINE ERROR:    MDS FieldError — below input, linked via aria-describedby
PAGE ERROR:      MDS AlertBanner variant="error" — above form, below nav
LOADING:         MDS Spinner (components) / MDS SkeletonLoader (pages)
                 Show after 200ms delay — never flash for fast operations
EMPTY STATE:     MDS EmptyState — always includes illustration, heading, body, CTA
PROGRESS:        MDS ProgressBar — show when operation exceeds 2000ms
                 Always show percentage and step count as text alongside bar
```

### 2.5 Overlay patterns

```
MODAL:     MDS Modal — user must complete action before continuing
           Max width 600px desktop. Never for simple confirmations or success states.

DIALOG:    MDS Dialog — brief confirmation, single decision, destructive confirmation
           Max width 480px.

DRAWER:    MDS Drawer (slides from right) — contextual detail, filter panels
           Width: 480px default, 640px for complex edit flows.

TOOLTIP:   MDS Tooltip — supplemental label for icon buttons, truncated text
           Never for required information. Never more than 2 lines.

POPOVER:   MDS Popover — rich supplemental content, triggered by explicit action only
           Never triggered on hover alone.
```

### 2.6 Data display

```
TABLE:      MDS DataTable — structured comparison, 3+ attributes
            Always: sticky header, visible sort state, empty state defined

LIST:       MDS List / MDS VirtualList (100+ items)

CARD GRID:  MDS CardGrid — visual browsing of courses, books, products
            4 col desktop / 2 col tablet / 1 col mobile

STAT:       MDS StatCard — single metric with label and optional trend

BADGE:      MDS Badge — system-assigned status labels
TAG:        MDS Tag — user-applied labels
            Never swap these. Badge = system. Tag = user.
```

---

## 3–8. Full specification

The following sections are included in the complete example pack:

**3. Behavioral contracts**
- Always-do rules with Meridian-specific additions
- NEVER list with 10 prohibited patterns specific to education products
- Destructive action protocol — complete implementation with exact copy

**4. Accessibility contracts**
- WCAG 2.1 AA commitment declaration
- Tier 1 automated enforcement checklist (11 rules, CI gate)
- Tier 2 human review checklist (8 rules)
- Tier 3 prohibited patterns (8 patterns identified through AT user testing)
- Education-specific section: MathML requirements, assessment controls, accommodation flags, AT targets

**5. Voice and copy standards**
- Brand voice definition and anti-examples
- Complete terminology table (8 terms with prohibited alternatives)
- Action label standards for all UI states

**6. Hybrid brand architecture**
- Complete tier assignment criteria for all three tiers
- Documented intentional divergences for Pathwright (Tier B) and Vantage (Tier C)
- Intentional divergence vs. accidental drift register
- Non-negotiables shared across all tiers

**7. Design system references**
- Figma, Storybook, token source, component library, icon library

**8. Change log + AI quick reference**
- Full version history
- 10-step AI agent decision protocol

---

## Get the complete example

The full Meridian Learning Group `designgov.md` includes all eight sections, the rendered HTML documentation viewer, and a step-by-step adaptation guide.

**[Get the complete example pack — $39 →](https://7511476758677.gumroad.com/l/ofiihn)**

---

*Meridian Learning Group is a fictional company created for illustrative purposes.*  
*designgov.md open standard: github.com/kenallangriffin/designgov*
