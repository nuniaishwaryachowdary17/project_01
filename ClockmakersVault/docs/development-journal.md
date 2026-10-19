# Implementation journal

These entries describe decisions made while preparing this artifact on October 18, 2026. They do not represent a reconstructed 17-day team history. Add actual team reviews and earlier records separately.

## Scope and navigation

Retained the proposal’s five-page flow, Track F, Investigation Pack, and both graduate bonus simulations. Kept all paths relative for opening from a ZIP or CODD. Native room radios retain state on the rooms page only. Cross-page room links enter the normal room picker rather than implying saved progress.

## Visual direction

Used deep green with brass and parchment, serif display headings, a quiet editorial layout, and original CSS illustrations. Replaced remote Cinzel/Inter loading with Georgia and system sans-serif to keep the deliverable self-contained. Shared variables centralize colors, spacing, timing, and type families.

## CSS organization

Kept a single linked `style.css` entry point. Split base tokens, layout, interactions, and motion into four imports to make the source readable and satisfy the requested file count. The trade-off is four additional local stylesheet requests.

## Puzzle and state design

Defined a consistent puzzle chain: IX gives 9, seven bells minus two gives 5, Volume IV gives 4, and three rings gives 3. The journal names their order. The code gate uses four sibling conditions. The gate protects both the visible success link and the target-driven door state. This closes an early design loophole where a direct hash could bypass the displayed link.

## Evidence board and assistance

Kept found checkboxes as board siblings so filters can read them without newer parent selectors. Checkbox flips also reveal ordinary text deductions for assistive technology. The Apprentice gives escalating authored hints. Each recommendation names a reason based on the selected room, avoiding false claims of live model inference or cross-page progress knowledge.

## Accessibility choices

Retained native inputs, radio semantics, summary disclosures, logical landmarks, and visible focus projected onto labels. Added a per-page motion pause control and OS reduced-motion overrides. Kept final transforms in state CSS so disabling animation still completes card flips and the vault opening.

## Executed checks and fixes

Executed local link/fragment checks, input-label checks, IDs/headings/landmarks inspection, HTML/CSS-only scope inspection, motion-rule presence, contrast calculations, and radio-code state analysis. Corrected room recommendations to use keyboard-operable links to the room picker. Added an always-visible found checklist so filtered cards cannot hide the focused checkbox’s visible label. See verification-results.json for exact executed results. Browser rendering, screen-reader behavior, W3C validation, deployed links, and classmate feedback remain for the team’s final review.

## Final review and vault cinematics (Aishwarya Nuni)

Reviewed the package against the grading rubric before submission. Removed the stale `SHA256SUMS.txt` (its hashes no longer matched once files changed) and added a `.gitignore` for macOS metadata. Added `css/vault-fx.css` as a separate module so the code gate in `interactions.css` stays untouched and easy to explain. The new layer only animates states that already exist: digits roll in when a radio changes, the halo brightens when the correct selector matches, and the open sequence (wheel, light, sparks, letter) hangs off the same `:target` rule as the door. Under Pause motion the letter, light and sparks skip to their end state instead of freezing invisible.

Applied two patterns from the course animation notes. The team page now uses the overlay card pattern: the base layer lifts and skews back while a "signature motion" panel slides up on a bouncy `cubic-bezier`. `:focus-within` and `tabindex="0"` give keyboard users the same reveal, and touch screens show the panel statically. A wrong code now also flashes the digit windows and rattles the door against its hinge. That needs `:has()` because the retry panel sits on the other side of the layout, so it is written as an enhancement on top of the existing shake.
