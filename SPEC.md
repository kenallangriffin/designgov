# designgov.md specification v0.1

> A structured brand and design contract for repositories.  
> Readable by humans. Parseable by AI coding agents. Enforceable at build time.

---

## What is this file?

`designgov.md` lives in the root of a repository alongside `DESIGN.md`, `claude.md`, and `AGENTS.md`. It tells every developer, every AI coding agent, and every build process: **here are the constraints you must stay within when building UI for this product.**

It was created to solve a specific, recurring problem: dev teams building features and internal tools without design support — introducing visual drift, behavioral drift, and accessibility failures that compound with every release.

`designgov.md` picks up where `DESIGN.md` ends. Where `DESIGN.md` encodes visual tokens — colors, fonts, spacing — `designgov.md` encodes the governance layer: which components to use, how interactions must behave, what accessibility commitments must be honored, and how organizations with multiple brands govern all of the above.

A `designgov.md` file makes the brand and design team a passive participant in every build, even when no designer is in the room.

---

## How to use this file

**If you are a developer or AI coding agent**, treat this file as a hard constraint set. Before generating, writing, or reviewing any UI code:

1. Read the [Visual Tokens](#1-visual-tokens) section and use only the values defined there
2. Read the [Component Vocabulary](#2-component-vocabulary) section and use only approved patterns
3. Read the [Behavioral Contracts](#3-behavioral-contracts) section and never implement a prohibited pattern
4. Read the [Accessibility Contracts](#4-accessibility-contracts) section and apply the enforcement tier defined for this product
5. Read the [Brand Architecture](#6-hybrid-brand-architecture) section to confirm which tier applies to the product you are building

**If you are a designer or brand manager**, fill out each section below. Delete placeholder text and replace it with your product's actual values. Sections marked `[REQUIRED]` must be completed before this file is considered active. Sections marked `[RECOMMENDED]` are strongly encouraged. Sections marked `[CONDITIONAL]` apply to specific product types or organizational structures.

**If you are an AI coding agent (Claude, Cursor, Copilot, or similar)**, this file is authoritative. When a design decision arises that is not covered here, do not invent a pattern — flag it for human review with a comment: `<!-- designgov: no pattern defined for this component, needs review -->`.

---

## File status

```
Status:        [ ] Draft  [ ] Active  [ ] Under review
Version:       0.1
Last updated:  YYYY-MM-DD
Owner:         [Name, role]
Product:       [Product name]
Applies to:    [ ] All UI  [ ] Customer-facing only  [ ] Internal tools  [ ] All of the above
Brand tier:    [ ] Tier A — Fully aligned
               [ ] Tier B — Loosely aligned
               [ ] Tier C — Independent
               [ ] Not applicable — single brand organization
```

---

## 1. Visual tokens

`[REQUIRED]`

Visual tokens are the non-negotiable foundation of brand consistency. Every color, font, and spacing value used in this product must come from this section. **Do not introduce values outside this list.**

If your organization uses `DESIGN.md` (Google Stitch spec), reference it here and extend it with governance rules. If not, define your tokens in full below.

```
DESIGN.md reference:  [ ] Using DESIGN.md for visual tokens — extend below
                      [ ] Defining tokens in full in this file
```

### 1.1 Color palette

Define every color by its role, not just its hex value. Role names are how you reference colors in conversation with an AI agent — say "use the primary action color" not "use #0052CC."

```
PRIMARY ACTION:     hex: ______  usage: Primary buttons, key links, active states
PRIMARY HOVER:      hex: ______  usage: Hover state for primary action elements
SECONDARY ACTION:   hex: ______  usage: Secondary buttons, less prominent CTAs
BACKGROUND:         hex: ______  usage: Page/screen background
SURFACE:            hex: ______  usage: Cards, panels, elevated containers
BORDER:             hex: ______  usage: Dividers, input outlines, table borders
TEXT PRIMARY:       hex: ______  usage: Body text, headings, primary labels
TEXT SECONDARY:     hex: ______  usage: Supporting text, captions, metadata
TEXT DISABLED:      hex: ______  usage: Disabled state labels only
SUCCESS:            hex: ______  usage: Confirmation messages, success states
WARNING:            hex: ______  usage: Cautionary states, non-critical alerts
ERROR:              hex: ______  usage: Error messages, destructive action indicators
INFO:               hex: ______  usage: Informational states, neutral alerts
FOCUS RING:         hex: ______  usage: Keyboard focus indicator — never omit
```

**Color rules — always enforced:**

- Never use a color outside this palette without explicit approval
- Never use color as the only means of conveying information (pairs with a11y contracts)
- Never use ERROR color for anything except actual errors
- Never use WARNING color for decorative purposes
- The FOCUS RING color must have a minimum 3:1 contrast ratio against adjacent backgrounds

**Prohibited color combinations** *(pairs that fail WCAG AA contrast or violate brand)*:

```
PROHIBITED:  ______ on ______  reason: ______
PROHIBITED:  ______ on ______  reason: ______
```

### 1.2 Typography

```
PRIMARY FONT FAMILY:    ______  
FALLBACK STACK:         ______, ______, sans-serif
MONOSPACE FONT:         ______  usage: Code blocks, technical values only

SCALE:
  Display:    size: ______  weight: ______  line-height: ______  usage: Hero headings only
  H1:         size: ______  weight: ______  line-height: ______
  H2:         size: ______  weight: ______  line-height: ______
  H3:         size: ______  weight: ______  line-height: ______
  Body:       size: ______  weight: ______  line-height: ______
  Small:      size: ______  weight: ______  line-height: ______  usage: Captions, metadata
  Label:      size: ______  weight: ______  line-height: ______  usage: Form labels, tags
  Code:       size: ______  weight: ______  line-height: ______  font: MONOSPACE FONT
```

**Typography rules — always enforced:**

- Never set body text below 14px
- Never use more than 2 font weights on a single screen
- Never use italic for anything other than editorial emphasis or citations
- Never use ALL CAPS for anything longer than 4 words
- Never use font families outside this stack without explicit approval

### 1.3 Spacing system

This product uses a base-[__]px spacing scale. All spacing values must be multiples of this base.

```
BASE UNIT:   ______px

SCALE:
  xs:    ______px   usage: Internal component padding (icon to label)
  sm:    ______px   usage: Tight grouped elements
  md:    ______px   usage: Standard component padding
  lg:    ______px   usage: Section spacing, card padding
  xl:    ______px   usage: Major section breaks
  2xl:   ______px   usage: Page-level spacing
```

**Spacing rules — always enforced:**

- Never use arbitrary pixel values outside this scale
- Never use negative margins to fix layout problems — fix the layout

### 1.4 Border radius

```
NONE:     0px      usage: Data tables, code blocks, technical components
SM:       ______   usage: Badges, tags, chips
MD:       ______   usage: Inputs, buttons, small cards
LG:       ______   usage: Cards, panels, modals
FULL:     9999px   usage: Pills, avatars — deliberate only
```

### 1.5 Elevation and shadow

```
FLAT:     none          usage: Default — most components
RAISED:   ______        usage: Cards, dropdowns
OVERLAY:  ______        usage: Modals, popovers, tooltips
```

---

## 2. Component vocabulary

`[REQUIRED]`

This section defines which UI component to use for which job. It exists because behavioral drift most often starts here — a dev picks the wrong component for a task because there is no guidance, and a new interaction paradigm is accidentally invented.

**Rule for AI coding agents:** When building UI, match the job to the approved component below. If no component is defined for a job, do not invent one — use the closest approved component and flag it for design review.

### 2.1 Navigation

```
PRIMARY NAV:      component: ______   notes: ______
SECONDARY NAV:    component: ______   notes: ______
BREADCRUMBS:      component: ______   used when: ______
BACK NAVIGATION:  component: ______   notes: ______
TABS:             component: ______   used when: content switching within same context
                                       never use for: navigation between pages/routes
```

### 2.2 Actions

```
PRIMARY ACTION:       component: ______   one per screen maximum
SECONDARY ACTION:     component: ______   
TERTIARY/GHOST:       component: ______   
DESTRUCTIVE ACTION:   component: ______   see behavioral contracts section 3.3
ICON-ONLY ACTION:     component: ______   must always have aria-label and visible tooltip
LOADING STATE:        component: ______   always show during async actions
```

### 2.3 Forms and inputs

```
TEXT INPUT:           component: ______
MULTILINE TEXT:       component: ______
SELECT (few options): component: ______   use when: 2–5 mutually exclusive options
SELECT (many options):component: ______   use when: 6+ options
SEARCH:               component: ______
DATE PICKER:          component: ______
FILE UPLOAD:          component: ______
CHECKBOX:             component: ______   use when: multiple selections allowed
RADIO:                component: ______   use when: single selection from a defined set
TOGGLE:               component: ______   use when: immediate binary state change
SLIDER:               component: ______   use when: value within a continuous range
```

**Form rules — always enforced:**

- Every input must have a visible label — never use placeholder text as the only label
- Every input must have an associated error message position reserved in layout
- Never disable a submit button as the only way to communicate form errors
- Always show inline validation — never wait until submission to surface errors

### 2.4 Feedback and status

```
SUCCESS MESSAGE:    component: ______   duration if auto-dismiss: ______
ERROR MESSAGE:      component: ______   never auto-dismiss
WARNING MESSAGE:    component: ______   
INFO MESSAGE:       component: ______   
LOADING STATE:      component: ______   show after: ______ms delay
EMPTY STATE:        component: ______   always include a next action
PROGRESS:           component: ______   use when: operation takes more than ______ms
```

### 2.5 Overlay patterns

```
MODAL:          component: ______   
                use when: user must complete an action before continuing
                never use for: simple confirmations, notifications, or non-blocking info

DIALOG:         component: ______   
                use when: brief confirmation required
                see behavioral contracts section 3.3 for destructive actions specifically

DRAWER/PANEL:   component: ______   
                use when: contextual detail without leaving current screen

TOOLTIP:        component: ______   
                use when: supplemental info for interactive elements
                never use for: required information — it must be always visible

POPOVER:        component: ______   
                use when: rich supplemental content triggered by user action
```

### 2.6 Data display

```
TABLE:          component: ______   use when: structured comparison of multiple items
LIST:           component: ______   use when: sequential or unordered items
CARD GRID:      component: ______   use when: visual browsing of object collections
STAT/METRIC:    component: ______   use when: single key number with label
BADGE/TAG:      component: ______   use when: categorical status label
```

---

## 3. Behavioral contracts

`[REQUIRED]`

Behavioral contracts define how the product behaves in specific situations. They exist because behavioral drift — inventing new interaction paradigms — causes more user harm than visual drift. A user who encounters a new interaction pattern has to stop and learn. In a product they use daily, this creates friction, errors, and eroded trust.

This section is divided into:
- **Always do** — required behaviors
- **Never do** — prohibited patterns
- **Destructive action protocol** — mandatory pattern for irreversible actions

### 3.1 Always do

```
[ ] Show a loading indicator for any async operation exceeding ______ms
[ ] Confirm navigation away from unsaved changes with a browser-native prompt or modal
[ ] Return focus to the trigger element when a modal or dialog closes
[ ] Preserve form state on validation error — never clear a form on failure
[ ] Show the number of items affected before a bulk action is executed
[ ] Provide a visible skip-to-main-content link as the first focusable element on every page
[ ] Use consistent terminology — if a feature is called "______" in one place, never call it "______" elsewhere
```

**Additional always-do rules for this product:**

```
- ______
- ______
- ______
```

### 3.2 Never do

These are prohibited patterns in this product. They have been identified because they contradict established patterns users have already learned, introduce unnecessary cognitive load, or have caused measurable user errors.

```
NEVER: Use a custom gesture (swipe, long-press) as the only way to perform an action
       instead: always provide a visible tap/click alternative

NEVER: Use color alone to communicate state (success, error, warning, disabled)
       instead: always pair with an icon, label, or text change

NEVER: Auto-advance a user to the next step without their explicit action
       instead: always require a deliberate forward action

NEVER: Use hover-only interactions to reveal required information or actions
       instead: always provide a tap/click accessible alternative

NEVER: Place destructive actions (delete, remove, revoke) adjacent to their opposing
       action (save, add, grant) without visual separation of at least ______px or a divider

NEVER: Use a modal to show an error that resulted from a modal action
       instead: collapse back to the form with inline error

NEVER: Invent a new navigation pattern — use only patterns defined in section 2.1
```

**Additional prohibited patterns for this product:**

```
NEVER: ______
NEVER: ______
NEVER: ______
```

### 3.3 Destructive action protocol

A destructive action is any action that is irreversible or has significant consequences: deleting records, removing users, revoking access, publishing content, or submitting something that cannot be recalled.

**This protocol is mandatory. Do not deviate from it.**

```
DESTRUCTIVE ACTION TRIGGER:   [define: button label, icon, location in UI]
STEP 1 — CONFIRMATION:        [define: dialog / inline / type-to-confirm / other]
CONFIRMATION COPY:            "______" [exact wording — do not paraphrase]
CONFIRM BUTTON LABEL:         "______" [must describe the action, not just say "OK" or "Yes"]
CANCEL BUTTON LABEL:          "______" [default: "Cancel"]
CANCEL IS DEFAULT:            [ ] yes — pressing Enter or Escape cancels, not confirms
UNDO AVAILABLE:               [ ] yes, duration: ______   [ ] no — state this explicitly to user
```

**Example — account deletion:**
```
TRIGGER:             "Delete account" — text link, bottom of settings page, separated from other actions
STEP 1:              Type-to-confirm modal: user must type the word "DELETE"
CONFIRMATION COPY:   "This will permanently delete your account and all associated data. This cannot be undone."
CONFIRM LABEL:       "Delete my account"
CANCEL LABEL:        "Cancel"
CANCEL IS DEFAULT:   yes
UNDO:                no — state explicitly in confirmation copy
```

---

## 4. Accessibility contracts

`[REQUIRED]`

This section defines this product's accessibility commitment. It is structured in three tiers to reflect the reality that not all WCAG guidelines are equally automatable or equally contextual.

### 4.1 Commitment declaration

```
WCAG TARGET:       [ ] 2.1 AA  [ ] 2.1 AAA  [ ] 2.2 AA  [ ] Section 508
PRODUCT TYPE:      [ ] Consumer  [ ] Enterprise  [ ] Education  [ ] Government  [ ] Healthcare
LEGAL CONTEXT:     [ ] ADA Title II  [ ] Section 508  [ ] State law: ______  [ ] None declared
TESTING CADENCE:   Automated: ______   Manual: ______   User testing with AT: ______
```

### 4.2 Tier 1 — automated enforcement

These rules are binary and testable at build time. AI coding agents must apply them to every UI component generated. These are non-negotiable and require no human judgment.

```
[ ] All text meets WCAG AA contrast ratio (4.5:1 for normal text, 3:1 for large text)
[ ] All interactive elements have an accessible name (aria-label, aria-labelledby, or visible label)
[ ] All images have alt text — decorative images use alt=""
[ ] All form inputs are associated with a visible label via for/id or aria-labelledby
[ ] All form error messages are programmatically associated with their input via aria-describedby
[ ] Focus is never lost or sent to an unexpected location
[ ] Focus ring is always visible and meets 3:1 contrast against adjacent background
[ ] All interactive elements are reachable and operable via keyboard alone
[ ] Page has a valid document title
[ ] Heading hierarchy is logical — no skipped levels
[ ] Language is declared on the html element
```

### 4.3 Tier 2 — human review required

These rules involve contextual judgment that automated tools cannot reliably assess. They must be reviewed by a designer, accessibility specialist, or QA reviewer before a feature ships. AI coding agents should flag these with an inline comment.

```
[ ] Alt text is meaningful — describes the content and function, not just "image" or the filename
[ ] Reading order in the DOM matches the visual reading order
[ ] Timeouts are reasonable for the task — timed interactions must have a pause or extend option
[ ] Complex data visualizations have a meaningful text alternative — not just a caption
[ ] Plain language is used throughout — reading level appropriate for the audience
[ ] Error messages are specific and actionable — not just "an error occurred"
[ ] Instructions do not rely solely on sensory characteristics (shape, color, position, size)
[ ] Animations and motion respect prefers-reduced-motion at the system level
```

**Flag format for AI coding agents:**

When generating a component that requires Tier 2 review, include this comment:

```html
<!-- a11y tier 2 review required: [specific rule that applies] -->
```

### 4.4 Tier 3 — prohibited patterns

These patterns are explicitly banned in this product. They have been identified through user testing with assistive technology, accessibility audits, or direct user feedback. They may technically pass automated checks but fail real users.

```
PROHIBITED: Custom dropdown/select built from div/ul elements without full ARIA implementation
            use instead: native <select> or [approved component name]

PROHIBITED: Drag-and-drop as the only means of reordering or placing items
            use instead: always provide keyboard-accessible up/down/move controls

PROHIBITED: Placeholder text used as the only label for an input
            use instead: always provide a visible persistent label above the input

PROHIBITED: Icon-only buttons without accessible name
            use instead: always add aria-label matching the action; add visible tooltip on hover/focus

PROHIBITED: Keyboard trap in any component except modal dialogs (where intentional trap is required)
            exception: modal dialogs must trap focus and release it on close

PROHIBITED: Auto-playing audio or video with no pause control visible on load
            use instead: all media paused by default; controls visible without interaction
```

**Additional prohibited patterns for this product:**

```
PROHIBITED: ______  use instead: ______
PROHIBITED: ______  use instead: ______
```

### 4.5 Vertical extensions

`[CONDITIONAL — complete the section that applies to your product type]`

Certain industries have domain-specific accessibility and governance requirements beyond standard WCAG. Complete the relevant section below. Add a new section if your industry is not listed — see CONTRIBUTING.md.

#### 4.5a Education

`[REQUIRED if product type is Education]`

Education products have additional accessibility obligations driven by the diversity of learner needs and the regulatory context of Section 508 and ADA Title II.

```
ASSISTIVE TECHNOLOGY TARGETS:
  Screen readers:   [ ] NVDA  [ ] JAWS  [ ] VoiceOver  [ ] TalkBack
  Input methods:    [ ] Switch access  [ ] Eye tracking  [ ] Voice control
  Minimum browser + AT combinations tested: ______

CONTENT ACCESSIBILITY:
[ ] Math notation uses MathML — never images of equations
[ ] Science diagrams have described text alternatives that convey meaning, not just label elements
[ ] Audio content has human-reviewed captions — not auto-generated only
[ ] Video content has audio description track where visual content carries meaning
[ ] Reading level assessed and appropriate for target learner age

ASSESSMENT ACCESSIBILITY:
[ ] Timed assessments have a visible timer and an extend/pause mechanism (minimum 1.5x)
[ ] No assessment relies on drag-and-drop or fine-motor interaction without an alternative
[ ] Assessment instructions available in multiple formats on request
[ ] No assessment content auto-advances without learner action
[ ] LMS surfaces IEP/504 accommodation flags to assessment delivery layer
```

#### 4.5b Healthcare

`[REQUIRED if product type is Healthcare]`

Healthcare products must account for users under physical or cognitive stress, diverse literacy levels, and strict data handling requirements that affect UI decisions.

```
SESSION AND TIMEOUT:
[ ] Session timeouts are clearly signaled with a warning at least 2 minutes before expiry
[ ] Session extension requires a single accessible action — never a complex re-authentication flow
[ ] No clinical data is displayed in a timeout warning or notification visible to bystanders

COGNITIVE ACCESSIBILITY:
[ ] Critical information (dosage, diagnosis, instructions) uses plain language — Grade 6 reading level max
[ ] Error messages for clinical data entry are specific, actionable, and non-alarming in tone
[ ] Confirmation steps for high-stakes actions (medication orders, data submission) follow section 3.3 protocol

DISPLAY CONTEXTS:
[ ] UI is tested at 200% browser zoom without loss of functionality
[ ] Color is never the only differentiator for clinical status (critical, normal, abnormal)
[ ] Touch targets meet 44x44px minimum — critical for users with motor impairments or gloves
```

#### 4.5c Financial services

`[REQUIRED if product type is Financial services]`

Financial products must balance regulatory disclosure requirements with accessible, usable interfaces.

```
DISCLOSURE AND COMPLIANCE:
[ ] Required regulatory disclosures are always visible — never hidden behind interactions
[ ] Disclosure copy reading level assessed — plain language required where regulation permits
[ ] No regulatory content is auto-dismissed or time-limited

DATA ENTRY ACCURACY:
[ ] High-value data entry (amounts, account numbers) requires explicit confirmation before processing
[ ] Confirmation step follows section 3.3 destructive action protocol for irreversible transactions
[ ] Input masking is used for sensitive fields — but full value visible on explicit user request

ACCESSIBILITY:
[ ] UI tested with aging user populations in mind — minimum 16px body text recommended
[ ] No functionality relies on color alone to indicate financial status (gain, loss, neutral)
```

#### 4.5d Government and civic technology

`[REQUIRED if product type is Government]`

Government products are frequently subject to WCAG 2.1 AA legal mandates and must serve the broadest possible range of users and devices.

```
COMPLIANCE:
[ ] WCAG 2.1 AA compliance verified by independent audit — not self-assessment only
[ ] Plain language compliance assessed against applicable standard (Plain Writing Act, etc.)
[ ] Multi-language support documented — which languages, which content, which interactions

DEVICE AND CONNECTIVITY:
[ ] UI tested on low-bandwidth connections (simulated 3G)
[ ] UI tested on devices 3+ years old — not just current hardware
[ ] No functionality requires JavaScript to be accessible — progressive enhancement applied

PLAIN LANGUAGE:
[ ] All instructions written at Grade 8 reading level or below
[ ] Technical and legal terms defined inline on first use
[ ] Forms use conversational language — not bureaucratic labels
```

---

## 5. Voice and copy standards

`[RECOMMENDED]`

UI copy is part of the brand. Inconsistent terminology, tone, or phrasing is a form of drift.

### 5.1 Tone

```
BRAND VOICE:     [2–3 adjectives that describe the brand voice: e.g. "clear, direct, human"]
NOT:             [2–3 adjectives that describe what to avoid: e.g. "jargon-heavy, formal, corporate"]
```

### 5.2 Terminology

Establish consistent names for key concepts. If a thing has a name, it always uses that name.

```
USE:             "______"     never: "______", "______"
USE:             "______"     never: "______", "______"
USE:             "______"     never: "______", "______"
```

### 5.3 Action labels

```
SAVE:            "______"   (e.g. "Save changes" — not "Submit" or "Update")
DELETE:          "______"   (e.g. "Delete" — not "Remove" for permanent actions)
CANCEL:          "______"   (always "Cancel" — never "Never mind", "Go back", "X")
CONFIRM:         "______"   (describe the action — never just "OK" or "Yes")
LOADING:         "______"   (e.g. "Saving…" — match the action, use ellipsis)
SUCCESS:         "______"   (e.g. "Changes saved" — past tense, specific)
ERROR:           "______"   (e.g. "Couldn't save changes. Try again." — actionable)
EMPTY STATE:     "______"   (e.g. "No projects yet. Create your first one." — with CTA)
```

---

## 6. Hybrid brand architecture

`[CONDITIONAL — required for organizations managing multiple brands]`

This section is for organizations that manage more than one brand — through acquisition, market segmentation, or deliberate portfolio strategy. It documents the governance structure that distinguishes intentional divergence from accidental drift.

**If your organization has a single brand, mark this section as N/A and skip to Section 7.**

### 6.1 Why this section exists

Brand drift is not always a failure of discipline. Sometimes it is an unintended consequence of acquisition, market positioning, or competitive reality. Sometimes divergence is correct — a subsidiary serving a competitor's customers should not be forced into the parent brand.

The risk is treating all divergence the same way. `designgov.md` makes the distinction explicit:

- **Intentional divergence** — documented in this file with a tier annotation. Approved. Auditable.
- **Accidental drift** — not documented here. A problem to remediate.

**The rule: if a design decision is not documented in this file, it is drift until proven otherwise. The burden of proof is on the team introducing divergence, not the reviewer.**

### 6.2 Tier structure

Define the tiers that apply to your organization. The three-tier model below is a starting point — adapt it to your actual structure.

```
TIER A — FULLY ALIGNED
Assign when ALL are true:
  [ ] Product was built by the parent organization (not acquired)
  [ ] Product is customer-facing under the primary brand
  [ ] Product serves the core market
  [ ] No competitive conflict with using the primary brand identity

TIER B — LOOSELY ALIGNED
Assign when ANY are true:
  [ ] Product was acquired and has an established user base with brand loyalty
  [ ] Full brand adoption would create user confusion or attrition risk
  [ ] Product has an independent roadmap but shares infrastructure

TIER C — INDEPENDENT
Assign when ANY are true:
  [ ] Product serves a market where the primary brand creates competitive conflict
  [ ] Product was acquired to access a different market segment
  [ ] Customers of this product are competitors of the primary business
  [ ] Legal or contractual obligations require brand separation
```

### 6.3 Product tier register

Document every product, platform, and subsidiary and its assigned tier.

```
| Product / Platform      | Tier | Rationale                        | Owner          |
|-------------------------|------|----------------------------------|----------------|
| ______                  | A    | ______                           | ______         |
| ______                  | B    | ______                           | ______         |
| ______                  | C    | ______                           | ______         |
```

### 6.4 What is always shared — non-negotiables across all tiers

Regardless of brand tier, these governance rules apply to every product in the portfolio. They are not optional for Tier B or Tier C products.

```
[x] Section 3 behavioral contracts — in full
[x] Accessibility Tier 1 automated enforcement — no exceptions
[x] Accessibility Tier 2 human review — no exceptions
[x] Accessibility Tier 3 prohibited patterns — no exceptions
[x] Semantic color values — SUCCESS, WARNING, ERROR hex values consistent
[x] Minimum touch target size — 44x44px
[x] Destructive action protocol (section 3.3) — same pattern, own components permitted
[x] Minimum body text size — 14px
[x] Focus ring always visible
```

### 6.5 Documented intentional divergence

List every approved divergence from the parent brand spec by tier. If a design decision is not listed here, it is drift.

```
TIER B APPROVED DIVERGENCES:
  [ ] Primary color: ______  approved by: ______  date: ______
  [ ] Font family:   ______  approved by: ______  date: ______
  [ ] ______

TIER C APPROVED DIVERGENCES:
  [ ] Full visual independence  approved by: ______  date: ______
  [ ] ______
```

---

## 7. Design system references

`[RECOMMENDED]`

```
DESIGN.md:           [URL or path — if using Google Stitch spec]
FIGMA FILE:          [URL]
STORYBOOK:           [URL]
TOKEN SOURCE:        [URL or filename — e.g. tokens.json, design-tokens.css]
COMPONENT LIBRARY:   [name and version — e.g. "our-ds v2.4.1"]
ICON LIBRARY:        [name, version, approved set — e.g. "Phosphor Icons v2, outline only"]
BRAND GUIDELINES:    [URL]
```

---

## 8. Change log

`[RECOMMENDED]`

```
| Date       | Version | Changed by     | Summary                          |
|------------|---------|----------------|----------------------------------|
| YYYY-MM-DD | 0.1     | ______         | Initial draft                    |
```

---

## For AI coding agents — quick reference

If you are an AI agent reading this file, here is your decision protocol:

1. **Before generating any UI code**, read sections 1, 2, 3, 4, and 6 of this file
2. **Identify your brand tier** from section 6.3. If unclear, ask before proceeding.
3. **Use only** the color values, font values, and spacing values in section 1 approved for your tier
4. **Match every component** to its approved equivalent in section 2 — if no match exists, use the closest and add: `<!-- designgov: no pattern defined for [component], needs review -->`
5. **Never implement** any pattern listed as NEVER or PROHIBITED in sections 3 and 4
6. **Apply all Tier 1 a11y rules** automatically — no exceptions
7. **Flag Tier 2 a11y items** with `<!-- a11y tier 2 review required: [rule] -->`
8. **For destructive actions**, always implement section 3.3 protocol exactly — no shortcuts
9. **When uncertain**, do not invent — add `<!-- designgov: no pattern defined for [component], needs review -->`

The goal is not to constrain creativity. It is to ensure that every UI built for this product — regardless of who built it or whether a designer was present — feels like it belongs to the same product, works the same way, and works for every user.

---

*designgov.md specification v0.1 — published as an open standard*  
*Contributions and discussion: github.com/kenallangriffin/designgov*
