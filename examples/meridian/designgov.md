# designgov.md — Meridian Learning Group
### Parent Brand Specification with Hybrid Architecture Guidance

> This file is the authoritative brand and design contract for all Meridian Learning Group products.  
> It includes guidance for subsidiary brands at each level of brand attachment.  
> Maintained by the Meridian Design Systems team.

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

## 3. Behavioral contracts

### 3.1 Always do

```
[x] Show MDS Spinner or SkeletonLoader for async operations exceeding 200ms
[x] Confirm navigation away from unsaved changes — beforeunload + MDS Dialog
[x] Return focus to trigger element when Modal, Dialog, or Drawer closes
[x] Preserve all form input on validation error — never clear on failure
[x] Show item count before bulk action: "Delete 14 courses?"
[x] Provide visible skip-to-main-content link as first focusable element on every page
[x] Use MDS Toast for all feedback — never build custom notification UI
[x] Minimum 44x44px touch targets on all interactive elements
```

**Meridian-specific rules:**

```
- Course and product titles are always Title Case — never sentence case or ALL CAPS
- "Learner" is always used for end users — never "student", "user", or "customer" in UI
- Progress always shown as percentage AND fraction: "67% complete (4 of 6 modules)"
- Certificates always show issue date and expiry date if applicable
```

### 3.2 Never do

```
NEVER: Custom dropdown from divs without full ARIA keyboard implementation
       use instead: MDS Select or MDS Combobox

NEVER: Color alone to indicate status in course or assessment contexts
       use instead: always pair with icon + text label

NEVER: Auto-advance learner to next lesson without explicit action
       use instead: always require deliberate "Continue" or "Next" action

NEVER: Hover-only interactions to reveal required actions or information
       use instead: always provide tap/click accessible equivalent

NEVER: Destructive and non-destructive actions adjacent without 40px separation or divider

NEVER: Auto-submit a form or assessment on last field completion
       use instead: always require explicit submission action

NEVER: MDS Modal for a success state after form submission
       use instead: MDS Toast + navigate to confirmation or return to list

NEVER: Invent a new navigation pattern — use only patterns defined in section 2.1

NEVER: Use "Submit" for course or assessment completion actions
       use instead: "Complete lesson", "Turn in assignment", "Finish quiz"

NEVER: Show a score or grade without context
       use instead: always show score, total, percentage, and pass threshold
```

### 3.3 Destructive action protocol

Applies to: deleting courses, content, user accounts, enrollments, certificates,
published materials, or any irreversible action.

```
TRIGGER:       MDS Button variant="destructive" — text only, never icon-only
               Position: separated from non-destructive actions by 40px or divider
               Never in primary action position

STEP 1:        MDS Dialog with warning icon in ERROR color
               Heading: "Delete [specific item name]?"
               Body: exact consequences — what will be lost, who is affected
               If affects other users: "This will affect [N] learners enrolled."

CONFIRMATION:  For actions affecting 10+ users OR published/public content:
               Type-to-confirm — user must type item name or the word "DELETE"

CONFIRM LABEL: Action-specific — "Delete course", "Remove learner", "Revoke certificate"
               Never: "OK", "Yes", "Confirm", "Proceed"

CANCEL LABEL:  "Cancel" — always. Never "No", "Go back", "Never mind"

CANCEL DEFAULT: Yes — Escape or Enter (without typing confirmation) cancels

UNDO:          Not available for most actions — state explicitly: "This cannot be undone."
               Exception: soft-delete with 30-day recovery — state recovery option in dialog
```

---

## 4. Accessibility contracts

### 4.1 Commitment declaration

```
WCAG TARGET:       [x] 2.1 AA
PRODUCT TYPE:      [x] Education
LEGAL CONTEXT:     [x] ADA Title II  [x] Section 508  [x] State law: varies by district
TESTING:           Automated: every PR (axe-core CI gate)
                   Manual audit: quarterly per product
                   AT user testing: biannually, minimum 3 participants
```

### 4.2 Tier 1 — automated enforcement

Applied via axe-core in CI. Every PR touching UI must pass before merge.

```
[x] All text meets WCAG AA contrast (4.5:1 normal, 3:1 large text and UI components)
[x] All interactive elements have an accessible name
[x] All images have alt text — decorative images use alt=""
[x] All form inputs are associated with a visible label
[x] All form error messages linked via aria-describedby
[x] Focus is never lost or sent to an unexpected location
[x] Focus ring always visible — never suppressed
[x] All interactive elements reachable and operable via keyboard
[x] Valid document title every page — format: "[Page] — [Product name]"
[x] Heading hierarchy logical — no skipped levels
[x] Language declared on html element
```

### 4.3 Tier 2 — human review required

QA sign-off required before any feature ships.
AI coding agents flag these with: `<!-- a11y tier 2 review required: [rule] -->`

```
[x] Alt text is meaningful — reviewed by QA, not auto-generated
[x] DOM reading order matches visual order — verified with screen reader walkthrough
[x] Timed assessments have pause and extend controls — design review required
[x] Complex charts have text alternative — reviewed by content team
[x] Error messages are specific and actionable — copy reviewed before launch
[x] Instructions do not rely solely on sensory characteristics
[x] Animations respect prefers-reduced-motion — verified in OS reduced motion mode
[x] New interaction patterns reviewed by accessibility specialist before launch
```

### 4.4 Tier 3 — prohibited patterns

Identified through Meridian accessibility audits and learner feedback. These may pass
automated checks but are known to fail real users.

```
PROHIBITED: Custom dropdown from divs without complete ARIA keyboard pattern
            fails consistently with JAWS + IE11 in institutional environments
            use instead: MDS Select (native select base) or MDS Combobox

PROHIBITED: Drag-and-drop as the only ordering or placement mechanism
            fails for switch access, fine motor impairments, keyboard-only users
            use instead: always pair with MDS ReorderList keyboard controls

PROHIBITED: Placeholder-only form labels
            disappears on focus, fails low-vision and cognitive load users
            use instead: persistent visible label above every input

PROHIBITED: Icon-only buttons without accessible name
            screen readers read "button" with no context — critical in tool-dense UIs
            use instead: MDS IconButton with aria-label + MDS Tooltip always

PROHIBITED: Auto-playing audio or video on page load
            disorienting for screen reader users, violates WCAG 1.4.2
            use instead: all media paused on load, controls visible without interaction

PROHIBITED: Keyboard trap outside of intentional modal focus management
            exception: MDS Modal intentionally traps and releases focus on close

PROHIBITED: Progress or score communicated only via chart or progress bar
            not perceivable by screen readers without text alternative
            use instead: always include text value alongside visual

PROHIBITED: Timed quiz or assessment with no visible countdown and no pause mechanism
            fails WCAG 2.2.1, creates barrier for processing speed disabilities
            use instead: MDS AssessmentTimer with countdown and pause/extend controls
```

### 4.5 Education-specific accessibility

```
ASSISTIVE TECHNOLOGY TARGETS:
  Screen readers:  [x] NVDA  [x] JAWS  [x] VoiceOver  [x] TalkBack
  Input methods:   [x] Switch access  [x] Voice control (Dragon)
  Minimum tested:  JAWS 2022 + Chrome, NVDA + Firefox, VoiceOver + Safari (macOS + iOS)

CONTENT:
[x] Math notation: MathML required — never images of equations
[x] Science diagrams: described text alternative required — not just element labels
[x] Audio content: human-reviewed captions required — auto-captions alone not acceptable
[x] Video: audio description required where visual content carries meaning not in audio
[x] Reading level: Flesch-Kincaid Grade 8 maximum for learner-facing copy

ASSESSMENT:
[x] All timed assessments: visible countdown + pause + extend option (1.5x minimum)
[x] No assessment requires drag-and-drop or fine-motor interaction without alternative
[x] Assessment instructions available in text, audio, and simplified format on request
[x] No assessment auto-advances — all progression requires explicit learner action
[x] LMS must surface IEP/504 accommodation flags to assessment delivery layer
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ TIER A  Full compliance required. CI gate blocks merge on Tier 1 failures.  │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER B — Pathwright                                                         │
│ Full Tier 1, Tier 2, Tier 3 required. Section 4.5 fully required.           │
│ Pathwright CI must integrate axe-core at same gate level as Meridian core.  │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER C — Vantage Professional                                               │
│ Tier 1 and Tier 2 required. Tier 3 prohibited patterns apply in full.       │
│ Section 4.5 assessment rules apply to all certification exam contexts.      │
│ Content rules apply where Vantage hosts learning content.                   │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 5. Voice and copy standards

### 5.1 Tone

```
BRAND VOICE:   Knowledgeable, clear, encouraging
               Confidence without condescension. Expertise without jargon.
               Meridian believes learning is a lifelong practice.

NOT:           Corporate, bureaucratic, cheerleader-enthusiastic
               Never "Congrats!" — use "Well done." Never "Amazing!"
```

### 5.2 Terminology

```
USE: "Learner"        never: "student", "user", "customer", "participant"
USE: "Course"         never: "class" — module = a part of a course
USE: "Instructor"     never: "teacher", "facilitator", "host"
USE: "Certificate"    never: "badge" — credential = broader category only
USE: "Enroll"         never: "register", "sign up", "join" for course entry
USE: "Complete"       never: "finish", "done", "submit" at course level
USE: "Dashboard"      never: "home", "portal", "hub"
USE: "Learning path"  never: "curriculum", "track" — "journey" approved in marketing only
```

### 5.3 Action labels

```
SAVE:     "Save changes"          never: "Submit", "Update", "Apply"
DELETE:   "Delete"                for permanent actions — never "Remove"
          "Remove"                for reversible list/group removal only
CANCEL:   "Cancel"                always — never "Never mind", "Go back"
CONFIRM:  Describe the action     never: "OK", "Yes", "Confirm", "Proceed"
LOADING:  Match the action        "Saving…", "Enrolling…", "Generating certificate…"
SUCCESS:  Past tense, specific    "Changes saved", "Learner enrolled"
ERROR:    Actionable              "Couldn't save. Check your connection and try again."
EMPTY:    With next action CTA    "No courses yet. Create your first course."
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ TIER A  Full terminology compliance required.                               │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER B — Pathwright                                                         │
│ Pathwright may use its own voice in product UI.                             │
│ Meridian terminology applies to Meridian catalog content surfaced within    │
│ Pathwright. Pathwright's own course creation UI may use its own terms.      │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIER C — Vantage Professional                                               │
│ Full voice independence. "Candidate" not "Learner". "Examination" not       │
│ "Course". Fully documented in Vantage's own designgov.md.                      │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 6. Hybrid brand architecture — decision guide

### 6.1 Tier assignment criteria

```
TIER A — Fully aligned
Assign when ALL are true:
  [x] Product was built by Meridian (not acquired)
  [x] Product is customer-facing under the Meridian brand
  [x] Product serves Meridian's core market
  [x] No competitive conflict with using Meridian visual identity

TIER B — Loosely aligned
Assign when ANY are true:
  [ ] Product was acquired with an established user base and brand loyalty
  [ ] Full brand adoption would create user confusion or attrition risk
  [ ] Product has independent roadmap but shares infrastructure

TIER C — Independent
Assign when ANY are true:
  [ ] Product serves a market where Meridian branding creates competitive conflict
  [ ] Customers of the product are competitors of Meridian's core business
  [ ] Legal or contractual obligations require brand separation
```

### 6.2 What is always shared across all tiers

Regardless of tier, these are non-negotiable across all Meridian Group products:

```
[x] Section 3 behavioral contracts — in full, no exceptions
[x] Accessibility Tier 1 automated enforcement — no exceptions
[x] Accessibility Tier 2 human review — no exceptions
[x] Accessibility Tier 3 prohibited patterns — no exceptions
[x] Semantic color values — SUCCESS, WARNING, ERROR hex values consistent
[x] Minimum touch target size — 44x44px
[x] Destructive action protocol (section 3.3) — same pattern, own components permitted
[x] Minimum body text size — 14px
[x] Focus ring always visible
```

### 6.3 Intentional divergence vs. accidental drift

```
INTENTIONAL DIVERGENCE (documented and approved — appears in this file):
  - Pathwright uses teal #007C91 as primary — approved, documented section 1.1
  - Vantage uses enterprise register — approved, documented section 5
  - Pathwright uses DM Sans — approved, documented section 1.2

ACCIDENTAL DRIFT (not approved — must be remediated):
  - An internal tool built by a dev team using Bootstrap defaults
  - A Vantage feature using a custom modal not following section 3.3
  - Any product introducing a color not documented with tier annotation
  - Any product using placeholder-as-label (prohibited, all tiers)

THE RULE:
  Intentional divergence appears in this file with a tier annotation.
  If a design decision is not documented here, it is drift until proven otherwise.
  The burden of proof is on the team introducing the divergence, not the reviewer.
```

---

## 7. Design system references

```
FIGMA:           https://figma.com/file/[meridian-design-system]
STORYBOOK:       https://design.meridianlearning.internal
TOKEN SOURCE:    tokens/meridian-tokens.json
COMPONENT LIB:   @meridian/mds v4.1.2
ICONS:           Phosphor Icons v2.0 — outline weight only
BRAND GUIDE:     https://brand.meridianlearning.internal
A11Y GUIDE:      https://a11y.meridianlearning.internal
PATHWRIGHT DS:   https://design.pathwright.internal (Tier B reference)
VANTAGE DS:      https://design.vantagepro.internal (Tier C reference)
```

---

## 8. Change log

```
| Date       | Version | Changed by          | Summary                                        |
|------------|---------|---------------------|------------------------------------------------|
| 2025-03-01 | 1.2     | Sarah Chen          | Added Tier C Vantage, updated a11y 4.5         |
| 2024-11-15 | 1.1     | Marcus Webb         | Pathwright Tier B annotations, typography      |
| 2024-06-01 | 1.0     | Sarah Chen          | Initial active version                         |
| 2024-03-10 | 0.1     | Design Systems team | Draft                                          |
```

---

## For AI coding agents — quick reference

1. **Identify your tier.** Tier A (Meridian core), Tier B (Pathwright), Tier C (Vantage). If unclear, ask before proceeding.

2. **Tier A:** this entire file applies in full. No substitutions.

3. **Tier B:** visual tokens may use Pathwright-approved substitutions documented in each section. All behavioral and accessibility rules apply in full.

4. **Tier C:** visual tokens are Vantage's own — consult Vantage's designgov.md. All behavioral and accessibility rules from this file apply in full.

5. **Component mismatch:** use the closest approved component and add:
   `<!-- designgov: no pattern defined for [component], needs review -->`

6. **Color not in palette:** do not use it. Flag it:
   `<!-- designgov: color not in approved palette, needs review -->`

7. **NEVER list:** if a pattern appears in section 3.2, do not implement it regardless of how it was specified.

8. **Every UI component:** apply all Tier 1 accessibility rules automatically. Flag Tier 2 items:
   `<!-- a11y tier 2 review required: [specific rule] -->`

9. **Destructive actions:** always implement section 3.3 exactly. No shortcuts.

10. **When uncertain:** do not invent. Flag and ask.

---

*Meridian Learning Group — fictional example for designgov.md specification v0.1*  
*Meridian Learning Group is a fictional company created for illustrative purposes.*  
*designgov.md open standard: github.com/kenallangriffin/designgov*
