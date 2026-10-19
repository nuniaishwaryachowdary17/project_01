# Bonus feature testing

## Feature 1 — The Apprentice

| Check | Repeatable action | Expected result | Evidence status |
| --- | --- | --- | --- |
| A1 Layout | Open Rooms at 375, 768, and 1280px | Hint grid reflows without clipping | Breakpoint/source structure checked; browser result pending |
| A2 Keyboard | Tab to each summary, press Enter/Space, then open nested hint | Each intent and hint tier is reachable | Native elements and labels inspected; keyboard run pending |
| A3 Reduced motion | Enable reduced motion and open all hints | All replies remain available without motion | Override/source checked; OS/browser run pending |
| A4 Flow | Use the vault hint link | Rooms opens at #apprentice | Local file/fragment verified |
| A5 Content | Reveal each hint tier | Room-specific nudge appears before answer | All authored tiers inspected |

AI mapping: authored intent and response templates simulate a conversational assistant. Original choice: hints stay in the apprentice’s narrative voice and remain voluntary. There is no generated response or model call.

## Feature 2 — Next Step cards

| Check | Repeatable action | Expected result | Evidence status |
| --- | --- | --- | --- |
| R1 Room context | Select Study, Tower, and Archive | Matching recommendation and evidence reason appear | Three sibling selectors and panel placement checked; browser run pending |
| R2 Responsive | Inspect all recommendations at 375, 768, 1280px | Panels stack on small screens and align at desktop | Grid/breakpoint source checked; browser run pending |
| R3 Keyboard | Use radio arrow keys, then tab to recommendation link | Recommendation follows room and the link is reachable | Native radio/link source checked; keyboard run pending |
| R4 Contrast | Check confidence text #c4d7b4 on #213b30 | At least 4.5:1, with a word and check mark | Contrast math passed; see verification-results.json |
| R5 Explainability | Read each recommendation | Action and journal-based reason are visible | Authored content inspected |

AI mapping: rule-based recommendation by selected room. Original choice: each card names its reason and uses an explicit confidence word. Confidence is an illustrative UI label, not a statistical estimate. The system does not claim to know how many clues the player found on a different page.
