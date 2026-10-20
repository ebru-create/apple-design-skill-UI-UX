# Web interface review

Hand-written companion to `SKILL.md` for websites, browser apps, and web content inside a
desktop/mobile wrapper. Apple HIG is a source of transferable design principles; the web
criteria below are not Apple platform requirements. Do not change pulled HIG text to adapt it.

## Route and establish evidence

- Identify the page's task, audience, brand, locale, existing tokens, and approved product rules.
  A website on an iPhone remains web content. A native wrapper may have separate native chrome.
- For accessibility, use WCAG 2.2 AA unless another target is supplied. Say when the review covers
  only selected criteria; the list below is not a complete conformance checklist or certification.
- For visual hierarchy, typography, color, and writing, open the relevant HIG files as needed
  through `hig-lookup.md`. Keep aesthetic advice distinct from web criterion failures.
- Use browser observations when available; code alone does not establish all rendered states.
  From a screenshot, review the visible layout and copy, and label pixel sampling as estimated.
  Mark keyboard paths, responsive states, and semantics not supplied or exercised as Not tested.
- Record the URL/selector or file:line, viewport in CSS pixels, zoom, state, input method, and
  measurements relevant to each finding. Never convert screenshot/device pixels directly into
  CSS pixels without the capture scale. Include foreground alpha and the composited background.

## Text and control measurements

| Check | Web rule | Evidence and exceptions |
| --- | --- | --- |
| Text contrast, SC 1.4.3 AA | At least 4.5:1 for normal text; at least 3:1 for large text | Large means at least 18 CSS pt regular (24 CSS px) or 14 CSS pt bold (about 18.67 CSS px). Size and weight both matter. Use the exact threshold, not rounded-down pixel values. |
| Control and graphic contrast, SC 1.4.11 AA | At least 3:1 against adjacent colors for visual information needed to identify controls/states and understand graphics | Check the relevant boundary, icon, or state. Inactive controls, unmodified user-agent controls, and essential presentations have exceptions; not every decorative border must pass. |
| Target size, SC 2.5.8 AA | At least 24 by 24 CSS px, or a qualifying exception | Measure the interactive target, not the icon. Evaluate spacing, equivalent control, inline, user-agent, and essential exceptions before declaring failure. A 44 CSS px target may be a usability recommendation, not this AA minimum. |

CSS uses 96 px per inch and 72 pt per inch; CSS pt are not native platform points or device
pixels. There is no universal WCAG minimum body font size. Judge readability in context and
test resizing; do not apply native iOS/macOS font minima to browser text.

For SC 1.4.3, incidental text (including inactive controls) and logotypes have exceptions. Do
not extend a logo exception to body copy. A small bold label still needs 4.5:1. Measure contrast
against the background actually behind the glyphs; a translucent surface, image, or gradient
needs compositing or checks of the relevant worst-case region, not two arbitrary hex samples.
Do not round a ratio up to the passing threshold. A source-only contrast result is conditional
on the supplied colors being the actual rendered, composited values.

## Interaction and responsive checks

- **Keyboard and focus:** verify actionable elements can be reached and operated, focus order
  follows the task, focus is visible, and dialogs/popovers manage focus and dismissal. Under
  SC 2.4.11 AA, author-created content must not entirely hide the focused component. For
  user-repositionable content, test its initial positions. User-opened content may obscure focus
  if the user can reveal the focused component without advancing keyboard focus (for example,
  dismissing an overlay with Escape). Complete visibility is a stronger target; partial overlap
  alone does not fail this criterion.
- **Reflow:** SC 1.4.10 AA tests vertically scrolling content at 320 CSS px equivalent width
  (for example a 1280 CSS px viewport at 400% zoom) without information/function loss or
  two-dimensional scrolling, except content whose meaning/use requires a 2D layout. The exception
  belongs to that content, not every paragraph on a page containing a table. For horizontally scrolling
  content, such as vertically written Japanese, test at 256 CSS px equivalent height.
- **Text resize:** check 200% enlargement without losing content or functionality under
  SC 1.4.4 AA, with its caption/image-of-text exceptions. This is separate from reflow testing.
- **Forms:** inspect accessible names, relationships, errors and recovery, correct input purposes,
  validation timing, and keyboard operation. Placeholder text alone is not a persistent label.
  Native HTML controls generally preserve useful semantics; verify custom controls rather than
  prescribing native Apple components. Automated scans cannot establish every criterion.
- **Authentication:** allow password-manager autofill and paste; do not interpret the ban on
  hard-coded credentials as a ban on user-controlled autofill. SC 3.3.8 AA allows mechanisms that
  assist cognitive tasks, as well as its alternative/object-recognition/personal-content exceptions.
  Do not remove a product's login gate merely because a generic onboarding guideline delays sign-in.
- **Motion and states:** inspect loading, empty, error, hover, focus and selected states when
  available. Consider reduced-motion preferences; distinguish animation preferences from a
  specific failure of pause/stop/hide or flashing criteria. A still image cannot prove motion behavior.
- **Navigation and appearance:** assess browser back behavior, links versus buttons, discoverable
  navigation, language, and zoom. A web theme switch or hamburger menu is not inherently a defect.
  Do not require an iOS tab bar, macOS app menu, SF font, or Liquid Glass for a browser page.

## Findings and verification

Use the evidence labels in `SKILL.md`. Keep a design suggestion separate from a criterion failure
even when they concern the same element. An observed numeric failure can have a runtime limit:
state exactly what is known rather than presenting the whole flow as tested. Preserve existing
branding and approved access/price rules; suggest changes to those as product decisions.

Example: supplied computed styles show a 16 CSS px bold label at a measured 3.5:1 on its actual
background. Report an Observed SC 1.4.3 AA failure in those supplied values, explain that the
large-text exception does not apply, propose a color meeting 4.5:1, and verify in the rendered
state. If only a compressed screenshot is available, do not invent the ratio or declare a pass.

## Sources

WCAG is the normative authority; Understanding pages explain application and exceptions.
Recheck the relevant source before relying on an unfamiliar exception or claiming conformance.

- [WCAG 2.2 standard](https://www.w3.org/TR/WCAG22/)
- [SC 1.4.3 Contrast Minimum](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)
- [SC 1.4.11 Non-text Contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html)
- [SC 2.5.8 Target Size Minimum](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html)
- [SC 2.1.1 Keyboard](https://www.w3.org/WAI/WCAG22/Understanding/keyboard.html)
- [SC 2.4.7 Focus Visible](https://www.w3.org/WAI/WCAG22/Understanding/focus-visible.html)
- [SC 2.4.11 Focus Not Obscured Minimum](https://www.w3.org/WAI/WCAG22/Understanding/focus-not-obscured-minimum.html)
- [SC 1.4.10 Reflow](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html)
- [SC 1.4.4 Resize Text](https://www.w3.org/WAI/WCAG22/Understanding/resize-text.html)
- [SC 3.3.8 Accessible Authentication Minimum](https://www.w3.org/WAI/WCAG22/Understanding/accessible-authentication-minimum.html)
