# CODD, GitHub, and presentation handoff

## CODD with WinSCP

1. Open your existing CODD connection using your own account.
2. Open the web-accessible directory used for your course pages, commonly `public_html`. Confirm the correct location in your account before transferring.
3. Upload the entire `Nuni_ClockmakersVault` folder without renaming CSS/images or flattening subfolders.
4. For Nirupam’s account, if uploaded under that exact folder, the expected URL is `https://codd.cs.gsu.edu/~nchitturi1/Nuni_ClockmakersVault/`. This is a proposed path, not a verified deployment. The leader’s account will have a different username.
5. Check `index.html`, `rooms.html`, `clues.html`, `unlock.html`, and `team.html` from the live URL. Hard-refresh after replacing CSS. Check capitalization: CODD paths are case-sensitive.
6. Verify the CSS, favicon, docs, and presentation downloads load. Use directory permissions 755 and file permissions 644 only if your course environment requires adjustments. Never use 777.
7. Paste the working URL into `links.txt`.

## GitHub from VS Code

Use an actual repository owned by the team and named `Nuni_ClockmakersVault`. Open the project folder in VS Code. If it is new, initialize Git. Stage only reviewed project files. Make a truthful initial commit such as `Add HTML and CSS escape-room implementation`, then create/publish the repository through VS Code or GitHub.

Review and improve the project in subsequent genuine commits, for example accessibility fixes or confirmed testing notes. Do not backdate commits or manufacture a 17-day history. If an existing team repository is available, use that repository and its real history instead of replacing it.

Verify the repository contains every required file and the README. If private, grant the instructor access using the course’s instructions. Paste its actual URL into `links.txt`.

## Presentation and recording

Use the provided PowerPoint and approximately 18-minute script. Show the real site, then open the actual HTML/CSS in VS Code. All team members participate. Use Zoom, Teams, or WebEx at 1080p or higher. Confirm the recording contains audio and legible code. Include one selected answer from each official Q1–Q11 block and all five official Q12 defense answers.

The official Q&A and presentation URLs returned retrieval errors during preparation. The defense guide provides implementation-specific preparation but does not claim to reproduce those unavailable questions. Check the official pages in your own browser before recording.

Upload the video to YouTube, with an unlisted setting if desired. Suggested title: `CSC 4370/6370 Project 1 — The Clockmaker’s Vault`. Put all three full names in the description. Test the link in a signed-out window and add it to `links.txt`.

## Final handoff

Confirm all three links, all team names/IDs, actual hours, the approved proposal, real Kanban evidence, and the final test results. Submit the links text file and any other required course deliverables to the designated iCollege Dropbox. Each member submits their required copy.
