# The Clockmaker’s Vault

An atmospheric escape room built with HTML and CSS. Search the Study, Clock Tower, and Archive, collect four digits, and open Elias Wren’s vault.

**Course:** CSC 4370/6370, Project 1  
**Track:** F — Escape Room Challenge  
**Extension:** Investigation Pack  
**Graduate bonus features:** AI Assistant Panel and Recommendation Engine UI  
**Folder / intended repository:** `Nuni_ClockmakersVault`

## Open the project

Extract the ZIP, open the `Nuni_ClockmakersVault` folder, and double-click `index.html`. No installation, build, API key, or internet connection is needed. You can also use VS Code Live Server. Keep the CSS and images folders beside the HTML files. Use a current Chrome, Edge, Firefox, or Safari browser.

## Pages and file integration

| File | Purpose | Assigned responsibility in proposal |
| --- | --- | --- |
| `index.html` | Briefing, visual clock, room route, instructions | Adithya Godavarthi |
| `rooms.html` | Three room selections, puzzles, tiered Apprentice hints, Next Step recommendations | Nirupamarayudu Chitturi; bonus integration assigned to Aishwarya Nuni |
| `clues.html` | Six flip cards, found markers, filters, readiness state | Adithya Godavarthi |
| `unlock.html` | Forty native radio inputs, correct/wrong attempts, animated vault and letter | Aishwarya Nuni |
| `team.html` | Leader, team roles, project details, time summary | Aishwarya Nuni coordinates; team confirms records |
| `css/style.css` | Shared stylesheet entry point importing the four modules below | Aishwarya Nuni |
| `css/tokens.css` | Design variables, typography, base elements, focus and utility rules | Adithya Godavarthi |
| `css/layout.css` | Grid/Flex regions, CSS illustrations, components, breakpoints | Aishwarya Nuni / Adithya Godavarthi |
| `css/interactions.css` | Native state selectors for rooms, evidence, and lock | Nirupamarayudu Chitturi / Aishwarya Nuni |
| `css/motion.css` | Keyframes, transitions, room scene motion (swinging bells, lantern sweep, lifting volume), scroll-driven reveals, cross-page view transitions, pause control, reduced motion | Nirupamarayudu Chitturi |
| `css/showcase-fx.css` | 3D orrery and embers (home hero), holo-foil card tilt, gilded borders, 3D evidence ring (clue board), found stamp, button sheen | Adithya Godavarthi |
| `css/vault-fx.css` | Vault cinematics: odometer digits, gilded halo, ready state, light flood, sparks, letter unfold | Aishwarya Nuni |

Every HTML page links to `css/style.css` and the local favicon. All navigation uses relative paths. No server includes are needed. `style.css` imports every module, so adding a module never changes the HTML `<link>`. Each source file has an attribution header and explanatory comments. The favicon is an additional SVG asset.

## Play-through

1. Start on the Briefing, then open Puzzle rooms.
2. In the Study, inspect the clock at IX and open the journal. The first digit is **9**.
3. Select Clock Tower with its radio control. Seven bells minus two silent bells gives **5**.
4. Select the Archive. The marked Volume IV gives **4**. The letter’s three seal rings give **3**.
5. Read the journal order: hour, sound, volume, seal.
6. On the Clue Board, turn cards with their checkbox controls and mark the four key clues as found. The readiness link appears. Try All, Found, Not found, and Key filters.
7. At The vault, choose **9 5 4 3**. The correct state shows “Open the vault.” Click it to read Wren’s letter.
8. Try an incorrect code to see the retry feedback. Reset digits or use the replay link to begin again.

Keyboard: Tab moves to native controls. Arrow keys change radio choices. Space toggles checkboxes. Enter or Space opens a summary. Focus rings are projected onto the visible labels. Evidence “found” controls are grouped before the flip controls in DOM order to keep sibling-selector state available. The checkbox’s accessible name identifies its clue. An always-visible notebook checklist keeps projected focus visible even when a filter hides a card.

## How the CSS works

- **Room selection:** three sibling radios share `name="room"`. A checked radio reveals its matching `.room-panel`. Native radio semantics are retained rather than imitating a scripted ARIA tab interface.
- **Reveals:** `details` and `summary` provide clue and hint disclosure with ordinary keyboard behavior.
- **Evidence:** filters and found markers are siblings of the evidence grid. Rules such as `#filter-found:checked ~ #found-hour:checked ~ .evidence-grid .evidence-hour` show only matching cards. Each flip also reveals an ordinary text deduction. Decorative 3D faces are hidden from assistive technology.
- **Code validation:** all forty digit radios share one form parent. The selector `#d1-9:checked ~ #d2-5:checked ~ #d3-4:checked ~ #d4-3:checked ~ .vault-layout` exposes the correct link. The same selector gates the `#open` door state. A manually entered hash cannot open a wrong combination.
- **Reset:** the native reset button returns all digit groups to zero. The replay link reloads the unlock page without its fragment. A visible retry message can remain while an incorrect combination is being edited, until the next successful combination or navigation.
- **State limitations:** CSS provides no persistent storage. Room selections, open disclosures, marked clues, and dials are local to each document. Cross-page links enter the destination’s normal initial state. Browser Back/Forward may restore form state according to the browser. Reload/replay starts a fresh attempt; private progress is never sent anywhere.
- **Security limit:** HTML/CSS source exposes the answer. The lock is a game interaction, not an authentication system.

## Design decisions and trade-offs

The palette uses deep green, warm brass, and parchment to suggest a clockmaker’s workshop. Georgia headings and a system sans-serif keep the site fully offline. CSS-built clocks, gears, books, bells, and the vault avoid image downloads and licensing dependencies.

Grid organizes the hero, room/sidebar split, evidence cards, team, and vault. Flexbox aligns navigation, controls, and metadata. Mobile is the base layout. At **600px**, cards and content begin sharing columns. At **1024px**, the full desktop layouts appear. Components use `minmax(0,1fr)` to allow long text to shrink and wrap.

The proposal planned a single stylesheet. The finished implementation keeps `style.css` as the single link and splits its contents into four readable modules to satisfy the request for more commented code files. Four small local imports add requests, but keep one clear entry point for the walkthrough. For a much larger production site, a combined distribution stylesheet would reduce that overhead.

## Motion and accessibility

The motion upgrade adds CSS-only 3D effects that are usually built with WebGL. The home hero has an armillary orrery: three brass rings orbit the clock using `transform-style: preserve-3d` with `rotateX`/`rotateZ` keyframes, while embers rise through the art. Route and evidence cards tilt in perspective on hover, with a foil sheen and a gilded border whose angle is animated through a registered `@property`. The Clue Board heading has a rotating 3D carousel of the six clue glyphs (hover pauses it). Each card's back is blank so mirrored text never shows. The vault adds odometer digits, a ready-state halo, a light flood, rising sparks, and a 3D letter unfold.

On the Rooms page the five sounding bells swing and send out a ring of sound while the two silent bells stay still, so the motion itself is a clue. A lantern beam sweeps each scene, the marked Volume IV lifts off the shelf, and switching rooms swings the new panel in on a shallow 3D arc. Cards rise into place as they scroll into view through `animation-timeline: view()`, wrapped in `@supports` so older browsers just show the content. Page-to-page navigation uses CSS cross-document View Transitions (`@view-transition`), which work on CODD over https in current Chrome and Edge. Opening the files locally skips them.

Pause motion freezes decorative loops but switches state-driven effects (scroll reveals, hint unfolds, the vault letter, the found stamp) to their end state, so nothing is left half-visible. `prefers-reduced-motion` removes all animation and transitions, and the view transitions are only declared inside `prefers-reduced-motion: no-preference`.

Motion includes gear rotation, pendulum movement, page/panel entrances, clue feedback, flip cards, brief wrong-code shaking, handle rotation, and the vault door sequence. Most movement uses `transform` and opacity. State styles exist independently of animations, so reduced motion still opens the vault and flips evidence.

Every page has a skip link, a named navigation landmark, a single h1, logical headings, and visible focus. Inputs remain in the accessibility tree. The “Pause motion” control pauses decorative animations for the current page. The OS `prefers-reduced-motion` preference removes animation and transitions. CSS illustrations have either descriptive alternatives or `aria-hidden` when decorative. Confidence labels include words and a check mark, not color alone.

### Motion map: each effect, the course-notes concept, and why it is there

| Effect | Page | Course-notes concept | Why |
| --- | --- | --- | --- |
| Clockwork gate: spinner winds, brass doors part | Briefing | Practice Problem 1 (spinner, reverse ring), `skewX`, multi-step `@keyframes` | Sets the story's tone in about 2 seconds and never blocks a click |
| Headline lines rise out of a mask | Briefing | Panel entrance, "guide reading order" | Reads top to bottom, landing on *time.* last |
| Rewind time: hover spins the hands backwards | Briefing | Transition vs animation | A transition reverses on its own when the pointer leaves, which a keyframe would not |
| Orrery rings, embers, gold shimmer | Briefing | 3D transforms, `perspective`, `preserve-3d` | Atmosphere without images or WebGL |
| Holo-foil tilt and gilded border on cards | Briefing, Clue board | 3D hover, overlay layering, `:focus-visible` | Hover and keyboard feedback that the card is a link |
| Room panel swings in on a 3D arc | Rooms | State change (`:checked`) plus a keyframe | Confirms which room changed |
| Five bells swing, two stay still | Rooms | Attention cue | The motion itself is the 7 − 2 = 5 clue |
| Volume IV lifts and glows | Rooms | Attention cue (glow) | Points at the third digit |
| Notebook toast: enter, hold, settle | Rooms | Practice Problem 4 (multi-step notification) | Confirms "you found a digit" without leaving the page |
| Apprentice typing cue before hints | Rooms | `steps()` timing function | Sells the simulated assistant (Bonus 1) |
| 3D evidence ring | Clue board | `preserve-3d`, `backface-visibility` | Shows all six clues at a glance |
| Found stamp, code strip drops in | Clue board | Add-to-cart feedback (scale/pulse), bouncy `cubic-bezier` | Rewards collecting the four key clues |
| Odometer digits, ready halo | Vault | Transition on state, `@property` | Each dial change is visible, and the correct code is felt before it is clicked |
| Door rattle and digit flash on a wrong code | Vault | Attention cue (subtle shake) | Clear "no" without a dead end |
| Wheel, light flood, sparks, letter unfold | Vault | Chained keyframes with delays | The payoff moment |
| Overlay cards slide up on hover and focus | Team | Overlay demo and Practice Problem 3 (`:focus-within`) | Same reveal for mouse and keyboard |
| Scroll reveals, page View Transitions | All | Panel entrance | Guides reading order between sections and pages |
| Brass scroll-progress line | All | Scroll-driven `@keyframes` (`animation-timeline: scroll()`) | Shows how far through a page you are |
| Logo clock turns one hour | All | Transition on `:hover` and `:focus-visible` | Small brand feedback on the way home |
| Flipped answers ink in | Clue board | Delayed keyframe, `filter: blur` + `scale` | The answer lands after the flip, not during it |
| Home clock starts running: ticking second hand, real-speed minute and hour hands | Briefing | `steps(60)` timing, the individual `rotate` property layered on `transform` | The workshop comes back to life once you open the case, while the Study clock stays stopped at IX for the puzzle |
| Signature writes itself | Vault | `clip-path` keyframe with a delay | Ends the story on a handwritten moment |

Shared timing lives in `tokens.css` (`--speed-fast`, `--speed-base`, `--speed-slow`, `--ease-out`). Interface feedback stays in the course's 150–400 ms range. Only the opening gate and the vault sequence run longer, because they are one-time story moments rather than repeated UI feedback.

## Bonus 1 — The Apprentice

**AI concept:** intent-based conversational assistance, simulated through authored disclosures.  
**Purpose:** reduce frustration without revealing the entire code at once.  
**Implementation:** four intent choices on the Rooms page. Each uses `details/summary` and optional nested hints. The vault links directly to the panel.  
**Original decision:** the clockmaker’s apprentice speaks inside the story, and the player controls hint depth.  
**Trade-off:** fixed replies cannot interpret free text. No AI model, API, or network request runs.

## Bonus 2 — Next Step recommendations

**AI concept:** an explainable, rule-based recommender, simulated with curated room-specific guidance.  
**Purpose:** guide the player through the journal order.  
**Implementation:** every room has an integrated recommendation with a suggested action, confidence text, and a reason. Selecting a room selects that room’s recommendation.  
**Original decision:** every recommendation names its evidence source. “High confidence” is an illustrative authored label, not a calculated probability.  
**Trade-off:** suggestions use the selected room’s context, not a hidden inference about collected clues.

At least three repeatable checks for each feature appear in `docs/bonus-tests.md`. Source checks are distinguished from browser checks awaiting team execution.

## Verification and remaining QA

`docs/verification-results.json` records the executed static checks, contrast calculations, and code-state analysis. The final offline Nu Html Checker 20.6.30 run also reports zero errors and zero warnings across the five HTML pages in `docs/html-validation.json`. `docs/qa-notes.md` records the method and open checks. These results are **not browser-rendering evidence**, W3C validation, screen-reader certification, or proof of a deployed site. The package still needs manual mobile/tablet/desktop checks, current-browser testing, W3C HTML/CSS validation, and classmate usability feedback. Capture actual screenshots after opening the site.

## Proposal and process evidence

`docs/Project_Proposal.docx` summarizes and formats the supplied proposal scope, with a separate implementation wireframe diagram. The original supplied text is preserved in `docs/proposal-source.txt`. This package does not create a new approval or signature. Keep the instructor-approved original if it differs.

`docs/development-journal.md` records implementation decisions from this preparation session. `docs/kanban.csv` is a handoff board based on the artifact’s current status, not historical Trello evidence. `docs/standup-log.csv` and `docs/time-tracking.csv` are ready for the team’s actual records. Fill the team page’s hours after confirming totals. Do not substitute these files for real standup or contribution history.

## Presentation

Open `presentation/Clockmakers_Vault_Presentation.pptx`. Use `presentation/walkthrough-script.md` for an approximately 18-minute run of show, live browser actions, and VS Code references. All three members have planned speaking parts. `presentation/defense-preparation.md` explains the implementation and trade-offs. The official Q&A page could not be retrieved during preparation, so verify the exact Q1–Q11 selections and five Q12 questions against the course guide before recording. No recording or upload is included.

## Deployment and submission

Read `START_HERE.txt` and `docs/deployment-guide.md`. Upload the folder contents to CODD with the HTML files at the URL root and preserve relative paths. Push the source to the team’s repository using genuine commits. Record and upload the presentation, then replace all three pending entries in `links.txt` with the verified CODD, GitHub, and YouTube URLs. Each member submits the required copy through iCollege.

## Significant AI assistance and attribution

OpenAI ChatGPT assisted substantially with the original HTML/CSS implementation, narrative and puzzle content, visual system, documentation, slide preparation, and static verification. The supplied proposal provided the concept, team identities, roles, scope, and course requirements. File comments identify **assigned responsibilities from the proposal**, rather than claiming that the named student independently authored AI-generated work. The team must review, understand, test, and be able to explain the submitted code. Actual contributions and hours should be recorded by the team.

Anthropic Claude assisted with the final review and the motion upgrade on October 18, 2026: the CSS-only 3D effects in `vault-fx.css`, `showcase-fx.css`, and the scroll-driven and page-transition rules in `motion.css`, plus the related README and QA updates. The visual direction was inspired by WebGL component galleries such as threeui.com, but no code was copied and no JavaScript, WebGL, or Three.js is used; every effect is rebuilt with CSS transforms, `@keyframes`, `@property`, and native element state.

## Assets and credits

No downloaded photos, icon library, web fonts, or third-party animation code are used. The decorative illustrations use CSS. The local SVG favicon is AI-assisted original code. Georgia/Times New Roman and system sans-serif fonts are referenced only as installed fallbacks. No external font files are distributed.
