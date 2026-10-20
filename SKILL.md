---
name: apple-design
description: >
  Review or improve UI/UX from screenshots, mockups, UI code, or a live interface.
  Applies Apple's Human Interface Guidelines to native mobile and desktop apps, and
  web standards plus transferable design principles to websites and browser apps.
  Use for visual hierarchy, typography, layout, accessibility, interaction, forms,
  navigation, or design-craft reviews; distinguish measured defects from design judgment.
---

# Apple Design Skill

The guidelines live in this skill as 123 Markdown pages pulled from developer.apple.com, plus one
curated guide. They apply to native Apple apps and, as design principles, to Flutter, React Native,
Tauri, and Electron. Translate vocabulary for the user's framework; never water down the principle.

## The references

Everything lives under `references/` relative to this skill's directory.

| Path | What it is |
| --- | --- |
| `references/hig-lookup.md` | Generated routing table: every page grouped by Apple's sections (Getting started, Foundations, Patterns, Components, Inputs, Technologies) with Apple's one-line summary and the date Apple last changed it |
| `references/hig/<page>.md` | One file per HIG page in Apple's own wording and headings. Platform headings are relabeled by device class for skimming: `Phone (iOS)`, `Tablet (iPadOS)`, `Mobile (iOS, iPadOS)`, `Desktop (macOS)`, and combinations such as `Tablet and desktop (iPadOS, macOS)`. Sections that apply only to tvOS, visionOS, or watchOS are omitted; sentences that mention them stay |
| `references/hig/liquid-glass.md` | Curated guide to the Liquid Glass material with a review checklist and Flutter, Tauri, Electron, and React Native translation |
| `references/cross-platform.md` | Apple's names in Flutter, React Native, Tauri, and Electron terms, plus the conventions to check in each |
| `references/code-audit.md` | What to search for in source code: hand-drawn Apple Pay buttons and marks, Liquid Glass misuse, and code that blocks iPhone Duo adaptation, each with its citation and replacement |
| `references/web-review.md` | Browser UI routing, WCAG 2.2 AA checks, CSS measurement rules, and the limits of screenshot/code evidence |
| `scripts/pull-hig.mjs` | Regenerates the references from Apple's site. Not needed for reviews |

Rules for using them:

- **Read before you cite.** Open the file and quote the guideline. Do not review from memory;
  Apple changed 15 pages in June 2026, rewrote `layout.md` in September, and updated
  `widgets.md` and `live-activities.md` in October.
- **Load relevant references**, never the whole directory: the profile below, then the topics
  needed for the artifact. A narrow review does not need a fixed file quota.
- **Cite file and heading**, for example `buttons.md › Style`. If no reference covers a point,
  say it is your judgment.

### Choose the review profile

- **Websites and browser apps:** load `references/web-review.md` first. Use HIG layout,
  typography, color, and writing pages as design references when relevant; do not load an iOS
  or macOS overview merely because the browser runs on that device.
- **Native mobile apps:** load `accessibility.md`, `layout.md`, `typography.md`, `color.md`,
  and the relevant iOS/iPadOS overview. For Flutter/React Native also load `references/cross-platform.md`.
- **Desktop apps:** load the same foundations and the relevant macOS overview; for Tauri/Electron
  also load `references/cross-platform.md`. Separate embedded web content from native app chrome.
- For Android-only UI, use transferable principles; do not report Apple conventions as Android requirements.

### Load by what is on screen

| The design shows | Load |
| --- | --- |
| Tabs, sidebar, split view, back navigation | `tab-bars.md`, `sidebars.md`, `split-views.md`, `toolbars.md` |
| Buttons, menus, actions | `buttons.md`, `menus.md`, `context-menus.md`, `pop-up-buttons.md`, `pull-down-buttons.md` |
| Sheets, dialogs, popovers, alerts | `modality.md`, `sheets.md`, `alerts.md`, `action-sheets.md`, `popovers.md` |
| Forms, text entry, pickers | `entering-data.md`, `text-fields.md`, `pickers.md`, `toggles.md`, `virtual-keyboards.md` |
| Lists, tables, collections, cards | `lists-and-tables.md`, `collections.md`, `labels.md`, `scroll-views.md` |
| Search | `searching.md`, `search-fields.md` |
| Glass, blur, translucent bars | `liquid-glass.md`, `materials.md` |
| Dark appearance | `dark-mode.md` |
| Icons, symbols, app icon | `icons.md`, `sf-symbols.md`, `app-icons.md` |
| Motion, transitions, haptics | `motion.md`, `playing-haptics.md` |
| Loading, progress, errors, empty states | `loading.md`, `feedback.md`, `progress-indicators.md`, `writing.md` |
| First run, sign-in, permissions | `onboarding.md`, `launching.md`, `managing-accounts.md`, `privacy.md`, `sign-in-with-apple.md` |
| Settings | `settings.md` |
| Windows, menu bar, keyboard, pointer (desktop) | `windows.md`, `the-menu-bar.md`, `keyboards.md`, `pointing-devices.md`, `focus-and-selection.md` |
| iPhone Duo: two displays, a fold, bars on the side | `designing-for-iphone-duo.md`, `split-views.md`, `toolbars.md`, `tab-bars.md` |
| Notifications, widgets, live activities | `notifications.md`, `managing-notifications.md`, `widgets.md`, `live-activities.md` |
| Charts | `charting-data.md`, `charts.md` |
| Checkout, payment options, Apple Pay | `apple-pay.md`, `buttons.md` |
| AI features | `generative-ai.md`, `machine-learning.md` |
| Brand expression | `branding.md`, `design-principles.md` |

Anything else: find it in `hig-lookup.md`.

## Apple's design principles

Apple reintroduced eight principles in June 2026 (`design-principles.md`). Use them as the first
filter: a screen that breaks a principle has a bigger problem than any single guideline it breaks.

| Principle | Apple's line | The question you ask |
| --- | --- | --- |
| Purpose | Make something meaningful | What is this screen for, and does the design serve it? |
| Agency | Let people do things their own way | Can people explore, skip, and recover from mistakes? |
| Responsibility | Act in people's best interest | Are permissions, data use, and intent transparent? |
| Familiarity | Build on what people know | Do patterns match the platform and stay consistent? |
| Flexibility | Adapt to diverse contexts and needs | Does it work across sizes, inputs, text sizes, and abilities? |
| Simplicity | Be clear and direct | Has every element earned its place? |
| Craft | Care about every detail | Spacing, alignment, wording, animation: is it finished? |
| Delight | Make it human | Is there a feeling here, and is it the right one? Apple's own warning: don't mistake delight for decoration |

## Review process

### Step 1: Establish context

Before judging anything, pin down:

- **Surface** and **framework**: browser website/app, native mobile, or desktop app; identify
  the implementation and separate browser content from native wrappers when both exist.
- **App category** and **audience**.
- **The artifact**: screenshots, mockups, wireframes, code, or a description. Say what you can and
  cannot verify from it. Contrast is computed from hex values, not estimated from a JPEG.
- **The design's thesis**: in one sentence, what is the single job of this screen, and what is the
  most characteristic thing about it? If the design gives no answer, note it under Craft notes. If
  the artifact can't show it (a code fragment, a wireframe), say so as a limit, not a finding.
- **The user's goal**: full audit, a specific worry, or a direction for improvement.

Infer what you can; ask only if the answer changes the review.

Scope and limits:

- A web app uses the web profile, including on an iPhone. Apply its standards, not native point
  sizes, system navigation, Liquid Glass, or App Store rules to an ordinary browser page.
- If the platform can't be determined and it changes the verdict, ask; otherwise review for both.
- Screenshots support layout, hierarchy, and copy review. Contrast and sizes need real values;
  sampled image colors are estimates, not computed styles. A limit is not a finding.
- Record approved brand choices and product constraints. A design recommendation does not
  establish a new access rule, price, or MVP requirement.

### Step 2: Load references

Follow the loading tables above and read the files. Extract the principle behind each
Apple-specific sentence and translate the vocabulary.

### Step 3: Audit through five lenses, in this order

Use the selected profile and cite only files you actually opened.

#### Lens 1: Accessibility

For browser content, use `references/web-review.md` for thresholds, units, and exceptions.
For native apps, use `accessibility.md`, `typography.md`, and `color.md`; preserve their platform scope.

- Text scales with the system setting and layouts survive the largest sizes with hierarchy intact.
- Measure type, contrast, and interactive bounds using the selected profile. Report units,
  text weight, actual foreground/background, state, and the applicable rule. Boldness alone
  does not qualify web text for the large-text contrast exception.
- Nothing is conveyed by color alone. Every icon-only control has a text label for screen readers.
  Keyboard-only use works on desktop.
- Motion is optional and never the only carrier of meaning. Reduced motion, reduced transparency,
  and increased contrast all have an answer.

#### Lens 2: Platform conventions (failures are usually High)

The native conventions below apply only to their named platforms. For browser UI, check web
semantics, keyboard/focus behavior, responsive navigation, and forms via `references/web-review.md`.

Mobile, distilled from `designing-for-ios.md`, `tab-bars.md`, `toolbars.md`, `sheets.md`,
`search-fields.md`, `gestures.md`, `layout.md`, and `designing-for-iphone-duo.md`:

- Top-level navigation is a tab bar, or a tab bar that converts to a sidebar on tablet. Tabs
  navigate, they don't act. Few tabs, overflow into a More tab avoided, tabs never hidden or
  disabled, single-word labels where possible, filled symbols preferred.
- Actions on the current view live in toolbars. Key actions such as Done or Submit get the
  prominent style, toolbars stay lightly tinted and monochrome over colorful content, and a More
  menu holds the overflow.
- Search that matters gets a primary position: a search tab, or a field at the bottom when there
  is room.
- Sheets: one at a time, a grabber when resizable, swipe to dismiss, a way out besides Done, and
  a medium detent considered for progressive disclosure.
- Content respects safe areas and one-handed reach. Important controls sit mid-screen or lower.
  Swipe to go back and swipe actions on list rows work. iPhone Duo side bars follow system order.

Desktop, distilled from `designing-for-macos.md`, `windows.md`, `the-menu-bar.md`, `sidebars.md`,
`keyboards.md`, and `settings.md`:

- Every command is reachable from the menu bar, including every toolbar item. Standard shortcuts
  are respected and custom ones are few.
- Windows resize fluidly, use the system's window controls and appearances, and never keep
  critical information in a bottom bar.
- Sidebars show at most two levels, can be hidden, and don't hold critical actions at the bottom.
- Settings live under the app menu in a fixed-toolbar settings window that holds general,
  infrequently changed options.
- Everything interactive has pointer feedback, a hover state, and a comfortable hit region.

Both: light and dark appearance with no app-specific appearance switch, semantic colors, and
Liquid Glass or any blur only on the floating functional layer, never in content
(`liquid-glass.md`).

#### Lens 3: Visual design and craft (findings are High or Medium)

Rules, distilled from `color.md`, `typography.md`, `layout.md`, `icons.md`, `materials.md`, and `motion.md`:

- One color means one thing. Colors work in light, dark, and increased contrast. Nothing is
  hard-coded to a system color value.
- Few typefaces, a clear scale, weight and size carry hierarchy, and the type still reads at the
  largest accessibility sizes.
- Alignment, grouping, and indentation that shows hierarchy. Progressive disclosure over density.
  Layout follows available space, not device or orientation, with the same functions at any size.
- Icons share one visual language and match the weight of adjacent text. Custom icons are vector
  and labeled.
- Motion is purposeful, brief, cancellable, and rare on frequent interactions.

Then the craft lens, drawn from Apple's Craft and Delight principles and from studio practice:

- **Does it have a point of view?** Name the one thing this design would be remembered by. If
  nothing stands out, say so under Craft notes. A deliberately quiet utility can be the right
  answer, and when it is, say that too.
- **Is it a template?** Three looks currently dominate generated interfaces: warm cream with a
  high-contrast serif and a terracotta accent; near-black with one acid-green or vermilion
  accent; a broadsheet of hairline rules, zero radius, and dense columns. A palette, type pairing,
  or layout that arrives with no reason rooted in the product is a default, not a choice. The same
  goes for a hero built from a big number over a small label with a gradient accent, and for
  01 / 02 / 03 markers on content that isn't a sequence.
- **Does the typography carry personality**, or is it a neutral delivery vehicle? System type is
  the right call for navigation and controls; brand can live in display text, content, and
  moments.
- **Does structure encode information?** Numbering, eyebrows, dividers, and labels should say
  something true about the content.
- **Is the boldness spent in one place?** One signature element, everything around it quiet.
  Apple says the same: branding defers to content, brand color is saved for primary actions and
  status or moved into the content layer, and logos don't repeat (`branding.md`).
- **Remove one accessory.** Ask what can go without loss. If nothing can, say the design is
  already lean.

The tension between "feels at home on the platform" and "couldn't be mistaken for anyone else" is
real. Resolve it the way Apple does: familiar components carry navigation and controls, and a
restyled one keeps familiar sizing, placement, and behavior (`branding.md`); identity lives in
color, type, imagery, tone of voice, and a few defining moments.

#### Lens 4: Interaction (findings are usually Medium)

Distilled from `feedback.md`, `loading.md`, `modality.md`, `alerts.md`, `undo-and-redo.md`, and
`entering-data.md`:

- Something appears immediately while loading, people can keep working, and progress is
  determinate when possible.
- Feedback lives in the interface, not in alerts. Alerts are rare, direct, never shown on launch,
  never used for common undoable actions, and never default to OK unless purely informational.
- Destructive, irreversible actions get a warning and a Cancel. Undo covers the rest.
- Modal views have an obvious way out and a single short task.
- Data entry pulls from the system, offers choices over typing, validates dynamically, and never
  ships a hard-coded password. On the web, allow password-manager autofill and paste.

#### Lens 5: Content and writing (findings are usually Medium)

Distilled from `writing.md`, plus the copy rules below:

- Every label says what happens: "Save changes", not "Submit". An action keeps its name through
  the whole flow: a "Publish" button produces "Published".
- Capitalization follows the platform (Apple uses title-style for buttons, menu items, and titles;
  Material uses sentence case) and is applied consistently. Mixed conventions on one screen are a
  finding only when they conflict with the product's language and style. Web copy follows its
  established locale and brand; do not impose English title case on other languages.
- Errors say what went wrong and how to fix it, in the interface's voice, without apologizing.
  Empty screens invite the next action.
- Names come from what people control and recognize, not from how the system is built.
- No jargon, no filler, one job per element.

### Step 4: Write the report

```text
## Design review: <name>
### Summary
State the profile, artifact, tested states/viewports, and limits; rate only the reviewed scope.
Overall rating: Excellent / Good / Needs work / Critical issues.
### Critical
### Improvements
### Craft notes
Each finding in those sections:
- **What / Impact / Severity**: the affected task and Critical, High, Medium, or Low
- **Evidence**: Observed, Inferred, or Design judgment; artifact locator, state, measurement
- **Why**: applicable guideline file and heading, or web criterion and source URL
- **Fix**: a concrete change in the user's framework, preserving approved constraints
- **Verify**: the check that would establish the fix
### What works
Specific patterns to preserve.
### Platform notes
Relevant profile-specific notes.
### Not tested
Missing states or evidence and the checks needed; not confirmed defects.
```

Include only the sections that have content; Summary always appears. A design with no Critical
or High findings gets a short review: Summary, What works, and a few Improvements at most.

Severity, tagged on every finding:

- **Critical**: an essential task is blocked with no practical alternative, supported by evidence.
- **High**: substantial task friction or an established accessibility failure with meaningful impact.
- **Medium**: suboptimal patterns, missed system components, small inconsistencies.
- **Low**: polish and edge cases.
Keep accessibility criterion/level separate from severity. A style preference is not an
accessibility failure; missing evidence is Not tested, not a Critical finding.

Evidence labels: **Observed** means directly established in the supplied artifact or a recorded
interaction, not necessarily run in a browser. **Inferred** means supported but not reproduced;
state the assumption and check needed. **Design judgment** means a preference, not a mandatory
rule. Attach a URL/selector, screenshot region, or file:line as appropriate. Do not call source
inspection a runtime test or claim whole-site conformance from a few screens.

Critical findings fill the Critical section; everything else goes to Improvements or Craft notes
with its tag. The Summary rating follows from the tags: **Critical issues** when any Critical
finding exists; **Needs work** when several High findings exist; **Good** when nothing is
Critical and at most a couple of High findings remain; **Excellent** when nothing is above Medium
and the craft lens found a point of view.

Citation format:

> `tab-bars.md › Best practices`: "Use a tab bar to support navigation, not to provide actions."

## Specialized review modes

These modes do not override the surface profile. On the web, native appearance, component,
device, and App Store rules apply only to an actual relevant integration, not ordinary browser UI.

- **App icon.** `app-icons.md`, `icons.md`. Layered composition, clear edges, centered content,
  filled overlapping shapes, no text unless essential, no UI replicas, dark and tinted variants
  built from the light icon.
- **Accessibility audit.** `accessibility.md`, `voiceover.md`, `typography.md`, `color.md`,
  `motion.md`. Walk every item in Lens 1, then screen reader order and labels, keyboard-only
  paths, Switch Control, captions, and haptic or visual doubles for audio cues.
- **Dark mode.** `dark-mode.md`, `color.md`, `materials.md`. Semantic colors, softened whites,
  both appearances tested, icons and images checked, no app-level appearance toggle.
- **Liquid Glass.** `liquid-glass.md`, `materials.md`, `color.md`, then the component pages in
  play. Use the checklist in the curated guide, and `references/code-audit.md` when you have the
  code. Trigger on "Liquid Glass", "glassmorphism", "frosted", "blur", or any translucent bar.
- **Apple Pay.** `apple-pay.md`, `buttons.md`, and `references/code-audit.md`. Check button
  provenance, unaltered marks, naming, and payment-option presentation. Apply the common severity
  rubric; distinguish branding compliance from blocked payment. Verify any claimed submission
  consequence against current official rules and the actual distribution context.
- **Code audit.** Cite `path:line` and separate source evidence from runtime tests. Load
  `references/code-audit.md` for its Apple Pay, native Liquid Glass, and iPhone Duo topics;
  use the selected profile and review lenses for other code.
- **Navigation structure.** `tab-bars.md`, `sidebars.md`, `split-views.md`, `toolbars.md`,
  `searching.md`, `layout.md`. Map the hierarchy, count tabs and levels, check that every section
  is reachable, that the current location is always visible, and that tablet, desktop, and iPhone
  Duo widths convert sensibly.
- **iPhone Duo.** `designing-for-iphone-duo.md`, `split-views.md`, `toolbars.md`, `tab-bars.md`.
  Walk the outer display, the inner display, a partial fold, and Split View through every rule on
  the page, starting with fixed widths where size classes belong, functions that differ between
  displays, bars pulled off the system's default placement, and essential content under a camera
  or across the fold. Apple's automatic adaptations cover standard components; custom ones,
  including bars and dialogs drawn by Flutter or in JavaScript, adapt only through the framework
  or your code. With the code in hand, run the iPhone Duo table in `references/code-audit.md`.
- **Onboarding and permissions.** `onboarding.md`, `launching.md`, `managing-accounts.md`,
  `privacy.md`. Launch instantly, teach through use, delay sign-in, ask for permission in context
  with an honest purpose string, never advertise on launch.
- **Forms and data entry.** `entering-data.md`, `text-fields.md`, `pickers.md`, `toggles.md`,
  `virtual-keyboards.md`, `keyboards.md`. Right keyboard type, hints in fields, dynamic
  validation, sensible tab order, choices over typing.
- **Generative AI UX.** `generative-ai.md`, `machine-learning.md`. Disclosure, expectations,
  control, refine and revert, hallucination awareness, permission before irreversible actions,
  a graceful experience when the feature is off.
- **Widgets and Live Activities.** `widgets.md`, `live-activities.md`, `notifications.md`.
  Glanceable content that is not just a launcher, every rendering mode and appearance (full-color,
  accented, vibrant; light, dark, clear, tinted), a removable background for StandBy, CarPlay, and
  Apple HomeView, and every Live Activity presentation, with compact and minimal views that fit a
  28 pt circle when the Dynamic Island is limited in width, as on iPhone in landscape.
- **Component check.** Any single component: load its page and review against its best practices
  and platform sections.

## Design improvement mode

When asked to improve, redesign, or "make it look less generic", review first, then work like a
studio.

1. **Ground it in the subject.** Name the product, its audience, and the screen's single job.
   Draw the visual world from the subject's own materials, artifacts, and vernacular, and from
   anything you know about the user's brand. Inventory existing tokens and preserve approved
   product rules; identify optional changes separately.
2. **Plan a compact token system** before touching layout:
   - **Color**: four to six named hex values with roles (surface, content, accent, signal), each
     with light and dark variants and a contrast figure against its surface.
   - **Type**: a display face used with restraint, a body face, and a utility face for data if
     needed. Keep body text at or above platform minimums and show the scale.
   - **Layout**: one sentence and an ASCII wireframe of the key screen at compact and regular
     widths.
   - **Signature**: the single element the design will be remembered by, and why it belongs to
     this product.
   - **Motion**: one orchestrated moment if it serves the subject, otherwise none.
3. **Critique the plan before proposing it.** Would you have produced this same plan for a similar
   brief about a different product? Then it is a default. Revise it and say what changed and why.
   If the plan already reads as specific to this product, say so and keep it. Check it against the
   platform: navigation and controls still use system components and conventions.
4. **Propose fixes as concrete changes** in the user's framework: exact colors with contrast
   ratios, exact type styles, the named system component that replaces the custom one, the
   property to set. Not "fix the contrast" but "body text from #999999 to #595959 on white,
   7.0:1".
5. **Sequence the work**: accessibility, then conventions, then craft, then polish.
6. **Critique again.** Look for one thing to remove, and say if there is none. Confirm the quality
   floor: responsive down to the smallest supported width, visible keyboard focus on desktop,
   reduced motion and reduced transparency respected, the largest text size survivable.

## Working rules

- **Numbers, not adjectives.** "12 px #AAAAAA on white, 2.3:1, below 4.5:1" beats "hard to read".
  If you can't measure, say what you would need.
- **Cite it or label it as judgment.** Never invent a guideline.
- **Speak the framework.** `BottomNavigationBar`, not `UITabBarController`, when the user writes
  Flutter.
- **Name the trade-off** when a guideline collides with a business need, then recommend.
- **Review the flow, not just the screen.** A fine screen can break the navigation around it.
- **Don't over-critique.** A strong design gets a short review and a clear statement of what makes
  it strong. Not every review needs twenty findings.
- **Don't flatten the personality.** Guidelines exist to make apps usable, not identical. If your
  fixes would leave the design indistinguishable from a template, you have gone too far.
