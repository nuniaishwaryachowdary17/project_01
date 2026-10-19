# QA notes

## Executed verification

Date: October 18, 2026. Method: local static analysis of shipped HTML/CSS, link resolution, contrast math, and tinycss2 syntax parsing and cssselect2 evaluation against the shipped DOM. These checks do not render the page.

- 305 source checks passed, with zero failures at this preparation stage. The JSON report lists each check.
- The compiled correct-code selector accepts exactly one of the 10,000 combinations in the actual DOM: 9543.
- All 256 evidence filter configurations and 64 readiness configurations passed compiled-selector checks.
- CSS declarations parsed and supported selectors compiled. Vendor marker pseudo-elements were omitted from selector compilation. This is not W3C validation.
- The door’s target state is also gated by all four digits.
- All five pages have one h1, landmarks, unique IDs, and labeled inputs.
- Local relative links and fragments resolve to existing targets.
- The source contains no scripts, embedded frames, inline event handlers, or javascript links.
- The CSS includes Grid, Flexbox, 600px/1024px breakpoints, more than three keyframes, focus styles, and reduced-motion overrides.

### Calculated contrast

| Text pair | Ratio |
| --- | --- |
| Body | 13.41:1 |
| Muted panel text | 7.66:1 |
| Brass label | 8.23:1 |
| Primary button | 9.13:1 |
| Confidence | 7.92:1 |
| Vault letter | 8.74:1 |

These calculations use the named solid color pairs. They do not replace visual checks of text over every gradient and interaction state.

## Additional offline HTML validation

Nu Html Checker 20.6.30 checked all five HTML pages. The final report contains zero errors and zero warnings. Two missing section headings found in the first run were corrected. `html-validation.json` preserves the final checker output. This is an offline checker version, not a current hosted W3C validation or browser layout test.

## Browser verification limit

No supported browser-control surface was available for this task. No browser rendering, mobile screenshots, cross-browser result, screen-reader audit, deployed-site check, or W3C validation pass is claimed. Complete and record the following before submission.

| ID | Action | Expected result | Actual result / tester |
| --- | --- | --- | --- |
| V1 | All pages at 375 x 812 | Readable single-column layout, no unintended horizontal overflow | To record |
| V2 | All pages at 768 x 1024 | Tablet columns wrap cleanly | To record |
| V3 | All pages at 1280 x 800 | Desktop regions fit and navigation stays clear | To record |
| V4 | 320px phone and 200% browser zoom | Content remains usable with reflow | To record |
| K1 | Tab through each page, then Space/arrow keys on inputs | Visible label focus, correct state, no keyboard trap | To record |
| K2 | Open/close every details and nested hint | Content appears in logical reading order | To record |
| S1 | Select each room | Correct room and recommendation appear | To record |
| S2 | Mark/unmark every evidence card; try all filters | Correct cards and empty states appear | To record |
| S3 | Flip each card | Both visual flip and text deduction update | To record |
| S4 | Mark four key clues | Readiness link appears, even if context clues are not marked | To record |
| L1 | 0000, 9542, 9543, reset, and replay | Wrong code retries, 9543 opens, reset closes and returns to zero | To record |
| L2 | Load unlock.html#open with default digits | Door stays closed | To record |
| M1 | Enable OS reduced motion | No looping or entrance motion; all states remain usable | To record |
| M2 | Activate Pause motion; open vault | Decorative loops pause; opening still completes | To record |
| B1 | Chrome, Edge, Firefox, Safari | Record browser versions and actual discrepancies | To record |
| A1 | Screen reader plus keyboard on radio/checkbox/details controls | Labels and disclosures make sense | To record |
| W1 | W3C HTML validator on every HTML page | Record actual messages and fixes | To record |
| W2 | W3C CSS validator on all stylesheets | Record actual messages and fixes | To record |
| U1 | Ask 2–3 classmates to find a clue and finish | Record real completion/hesitation observations | To record |

## Evidence capture

Capture actual desktop, tablet, and phone views after QA. Add a screenshot or GIF of the open vault and evidence filters for the README/showcase. Keep browser names, versions, viewport dimensions, findings, fixes, and retest results in this document. Do not describe wireframes as screenshots.
