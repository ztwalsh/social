# Build log

An editorial layer on top of git history across every project under
`~/sites/personal-projects`. Commits are the source of truth; this file is
"what changed and why it matters to someone who doesn't have the repo open" —
the raw material for weekly social posts.

- **Written by:** the `social-log` skill, triggered by a `PostToolUse` hook after
  every commit. The hook drops a `status: stub` block; the skill rewrites it
  into an enriched entry.
- **Read by:** the `social-draft` skill, weekly, to draft posts.
- Newest entry first. Once this file gets long, older years move to `log/2026.md`.

Entry format lives in
`Skills/agent-skills/social/social-log/reference/entry-format.md`.

<!-- entries below -->

## 2026-09-12 09:13 · voice-capture · a5b20f0
**What:** Fixed an ugly, always-visible scrollbar in the transcript window that Apple's own recommended one-line fix didn't actually fix, once tried live.
**Why it matters:** Second time this project has hit "the documented API for this just silently doesn't work" in this particular app's unusual setup — worth noticing as a pattern, since it means anything that looks visually wrong here is worth actually testing rather than trusting the fix on paper. Had to reach one layer deeper into the underlying macOS toolkit to force the real fix.
**Shareable:** no — too small/technical to stand alone.
**Tags:** #bugfix #ui #polish
_5 files changed, 42 insertions(+) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 08:57 · voice-capture · 7b48a0a
**What:** Replaced the generic macOS-blue "OK" button and mis-aligned header on the first-run setup screen with real buttons designed to match the rest of the app — solid black/white fill for the main action, a bordered style for secondary ones — since the app's whole visual language deliberately avoids color except for two very specific meanings (red = recording, green = improved).
**Why it matters:** A screenshot review caught what code review couldn't: the setup screen technically worked but looked like a generic system dialog bolted onto a custom-designed app, which undercuts the effort put into everything else. Small detail, but exactly the kind that separates "looks handmade" from "looks default."
**Shareable:** yes — before/after of the setup screen, generic blue button vs. the new matching style.
**Tags:** #polish #ui
_3 files changed, 75 insertions(+), 20 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 08:44 · voice-capture · 16f3b8d
**What:** Fixed a weird visual glitch spotted live: two entries in the transcript list that looked identical, where hovering over one made the *other* one light up instead.
**Why it matters:** Classic case of a bug that's invisible in the code but obvious the instant you touch the actual app — two dictations happened to land in the same minute in the same app, and the list was accidentally using "time + app" as each row's unique identity instead of something that's actually always unique. Screen-shared feedback caught it in seconds; it would've been easy to miss just reading the source.
**Shareable:** no — too small/technical to stand alone.
**Tags:** #bugfix #ui
_1 file changed, 12 insertions(+), 1 deletion(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 08:39 · voice-capture · 9aa8b8c
**What:** Added the small interaction details that separate "functional" from "feels designed": buttons on each transcript card now fade in only when you hover over it instead of cluttering the view all the time, cards animate smoothly open instead of snapping, new items settle into place with a soft rise instead of popping in, and the tab switcher's highlight slides between tabs instead of jumping.
**Why it matters:** None of these change what the app does — they change how it feels to use, which is the whole point of a dedicated polish pass. Small, deliberate motion is what makes an interface feel considered rather than assembled.
**Shareable:** yes, once bundled with the rest of the polish pass — a short before/after clip of hover-reveal and the sliding tab would read well.
**Tags:** #polish #ui #motion
_3 files changed, 39 insertions(+), 4 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 08:32 · voice-capture · 84e3f84
**What:** Swapped every piece of text in the dictation app — the floating pill and the whole history window — from the generic system font over to the actual typeface (Geist) the design called for from the start, with the right weight and letter-spacing in each spot instead of guessed approximations.
**Why it matters:** First step of a broader "make it actually look designed, not just functional" pass. The font files only existed in a web format that doesn't work in a native Mac app, so had to extract real weight variants from them by hand before any of this was possible — the unglamorous prerequisite before the visible payoff.
**Shareable:** no — a font swap alone isn't visually dramatic enough to post; better bundled with the fuller polish pass once it's done.
**Tags:** #polish #ui
_14 files changed, 145 insertions(+), 49 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 08:05 · voice-capture · 1f42957
**What:** Added a second way to dictate: click the menu bar icon once to start recording hands-free (no key to hold down), click again (or a stop button on the floating pill itself) to finish. The icon itself turns red for as long as it's listening, in either mode, so you can tell it's live even with every window covered.
**Why it matters:** The original hold-a-key method is great for a quick sentence but awkward for anything longer — this is the "start it and keep typing/thinking while it listens" mode. Found a fun bug building it: macOS reports which mouse button you clicked on a menu bar icon backwards from what its own documentation implies, so left and right click were swapped until tested by hand.
**Shareable:** yes — screen recording clicking the menu bar icon to start, the wider pill with its stop button, clicking stop, text landing.
**Tags:** #new-feature #ui #macos
_5 files changed, 213 insertions(+), 39 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 07:42 · voice-capture · bd8242a
**What:** Turned the dictation app from "something I run from Xcode" into something installable: a real first-run setup screen that checks all three permissions live and tells you exactly what to click, working Launch-at-Login and debug-audio toggles in Settings, an activity log for when something goes wrong, and a one-command script that builds a double-clickable app.
**Why it matters:** This is the gap between a working demo and something you'd actually trust to run every day — including the unglamorous but important bit: if you revoke one of its permissions by accident, it notices immediately and tells you, and un-revoking it works again without restarting the app. Tested that exact scenario live, both directions.
**Shareable:** yes — screen recording of the setup screen catching a missing permission live, and toggling it on/off to show the app adapting without a restart.
**Tags:** #new-feature #onboarding #macos
_13 files changed, 568 insertions(+), 55 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 07:24 · voice-capture · 7000f5f
**What:** Built the window where dictated transcripts actually live: a sidebar with an overview dashboard (a chart of captures per day, this week vs last), a searchable browsable list of everything ever said, a "read the raw file" document view, and a settings page — plus the menu bar icon needed to open any of it, since until now the app had no way in besides the hotkey itself.
**Why it matters:** The dictation app was "type by voice" only — the words landed in whatever app you were using but there was no way to go back and find, copy, or clean up something you said last week. This is the piece that makes a session's output actually yours to manage afterward, not just a one-way fire-and-forget. Caught a real bug along the way too: search worked in the card-list view but silently did nothing in the "read the file" view — found only by trying it, not by reading the code.
**Shareable:** yes — screen recording browsing the window: overview stats/chart, searching for a phrase, switching to the document view, deleting a card.
**Tags:** #new-feature #ui #macos
_12 files changed, 1225 insertions(+), 9 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 06:59 · voice-capture · 7d0d5a7
**What:** Fixed the dictation app's "Reduce Motion" accessibility support, which looked right in code but silently did nothing when actually toggled on — found by testing it live rather than trusting the implementation.
**Why it matters:** A neat lesson in the gap between "the code says it should work" and "it works": the app was checking Apple's standard SwiftUI signal for the system's Reduce Motion setting, but that signal never reached this particular floating panel because of how it's built (a background panel that never becomes the active window). Reading the setting a different, lower-level way fixed it. A feature that silently no-ops for the people who most need it is worse than not having the feature at all.
**Shareable:** no — too in-the-weeds to stand alone as a post.
**Tags:** #accessibility #bugfix
_1 file changed, 16 insertions(+), 1 deletion(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 06:35 · voice-capture · ecff2b9
**What:** Swapped the dictation app's plain placeholder box for the actual designed UI: a floating pill that shows a real waveform while listening, a shimmering "Transcribing" label, and shake-and-message error states — matching a design/motion spec written earlier in the project, in both light and dark mode and with Reduce Motion support. Also fixed a real transcription bug found only by testing on real hardware: Apple's on-device speech engine was silently dropping everything said before a mid-sentence pause, so swapped to Apple's newer long-form engine instead.
**Why it matters:** This is the "does the polish actually work" phase, and almost every fix here came from watching the real thing on a real Mac rather than from re-reading the spec: the waveform's motion looked like stop-motion because its smoothing rode the audio hardware's own jittery timing instead of a steady clock; the pill's shadow had a nasty rectangular halo from AppKit's own default window shadow; and it stayed stuck on one monitor in a three-monitor setup because it never re-checked where the cursor actually was. Each was invisible from the code and only showed up by trying it.
**Shareable:** yes — screen recording of a full dictation showing the waveform responding to voice, the transcribing shimmer, and an error state shake; before/after if a stop-motion vs. smooth waveform clip can be captured.
**Tags:** #ui #motion #bugfix #ai
_7 files changed, 702 insertions(+), 88 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-11 16:05 · voice-capture · 417efd3
**What:** Actually ran the Mac dictation app end to end on real hardware for the first time: held the hotkey, spoke, released, and the transcribed sentence landed in TextEdit. Also caught and fixed a bug in the app's own latency counter — it had been timing from when you first pressed the key (so it counted the time spent talking) instead of from release, which made the release-to-text number look 5-10x worse than reality.
**Why it matters:** This is the moment a proof-of-concept either works or doesn't, and it worked — the full loop (hotkey → record → transcribe → insert → log) is real, not just a plan. And the timing fix matters because a self-reported number that's wrong is worse than no number: once corrected, release-to-text came in at 0.53s for a 15-word sentence, comfortably under the 1.5s target.
**Shareable:** yes — screen recording of holding the hotkey in TextEdit and watching the text appear, plus the corrected terminal timing line.
**Tags:** #milestone #macos #ai
_2 files changed, 8 insertions(+), 5 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-11 15:55 · voice-capture · aefd92c
**What:** Ran the last untested piece of the Mac dictation app's de-risking phase: fed real 10-second recordings of my own voice to Apple's on-device speech recognizer and timed it, three separate takes.
**Why it matters:** The whole app hinges on transcription being fast enough that dictating feels instant rather than like waiting on a spinner. The budget was under 1.5 seconds for a 10-second clip; it came back at 0.37–0.56 seconds — 18 to 28 times faster than real time, with clean transcripts and no hallucinated words on silence. That closes out the last open question from the app's proof-of-concept phase, so it's cleared to move on to actually running the full loop end to end.
**Shareable:** yes — the terminal output showing the three PASS runs with realtime multipliers.
**Tags:** #experiment #ai #macos
_1 file changed, 17 insertions(+), 6 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-11 11:10 · assistantOS · 4b019a7
**What:** Bulk-imported a dozen meeting transcripts (1-1s, all-hands, review sessions) into the assistant project's notes.
**Why it matters:** Housekeeping, not a feature — feeding meeting context into the assistant so it has real material to work from. Nothing here is shareable.
**Shareable:** no
**Tags:** #housekeeping
_13 files changed, 1139 insertions(+) · branch `main`_
status: enriched _(reconstructed from commit metadata — repo/SHA not locally reachable)_

## 2026-09-10 16:44 · voice-capture · 910a3bc, 63b6c3c
**What:** Proved out the two hardest unknowns for the Mac dictation app on real hardware, and got the throwaway "walking skeleton" compiling cleanly. Test one: the small floating "listening" panel never steals keyboard focus — confirmed in native Mac apps, a Chromium browser, and Slack (Electron). Test two: a matrix of how to insert transcribed text into eight target apps — pasting via the clipboard works in all eight; the tidier "accessibility API" route works in only four, and silently fails in Terminal while reporting success.
**Why it matters:** This is the phase that decides whether the idea is even feasible on macOS, which offers no supported way to type into another app or to show UI without grabbing focus. Both came back green: focus stays put, paste is the insertion path to build on. The sharp lesson — a "success" result can't be trusted, the app has to read the text back to confirm it landed. A browser password field even accepted fake keystrokes without the OS flagging it, so the app has to dodge password fields itself.
**Shareable:** yes — the 8-app × 3-strategy insertion matrix plus the focus-test output. Screenshot the terminal showing PASS across Notes / Chrome / Slack, the LANDED / NOT FOUND matrix, and the "SECURE INPUT IS ACTIVE" detection line.
**Tags:** #experiment #infra #dx
_2 files changed, 81 insertions(+), 23 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-10 16:43 · assistantOS · c89e790, f5cb131, 7e9ea3c, 52676bb
**What:** Selecting text in assistantOS and right-clicking now offers Copy as Markdown, Rich Text, or Plain Text — in both the rich editor and the read-only document view, matching the whole-file copy menu the viewer already had but scoped to the selection. Also fixed the reason the menu did nothing at first: opening the context menu cleared the selection, so every copy was a silent no-op; the selection is now captured the instant you right-click. And dropped the coloured tint from the project board's four column-header icons, since the layout already conveys status.
**Why it matters:** Pulling a few paragraphs out of a doc and getting clean Markdown back — not HTML soup, not literal markup — is a small thing you feel every time it fails. The no-op bug is the classic kind that demos perfectly while nothing actually reaches the clipboard.
**Shareable:** yes — right-click Copy-as menu open on a selection in the editor; before/after of pasting that selection somewhere plain (clean markdown vs raw HTML).
**Tags:** #new-feature #bugfix #ui
_4 commits, ~505 insertions / 159 deletions · branch `editor-copy-and-swimlane-icons`_
status: enriched

## 2026-09-08 20:21 · assistantOS · 34f7c73
**What:** The "push to Google Drive" button in assistantOS now turns Markdown files into properly formatted Google Docs instead of a wall of literal `#` and `**`. Markdown is rendered to HTML first and handed to Drive's importer as an .html upload, so Google builds real headings, lists, tables, and bold/italic. Other file types keep the plain-text path.
**Why it matters:** Before this, every doc pushed to Drive needed reformatting by hand before it was fit to share — the markup came through as raw text. Now it arrives as a real Doc. Small integration fix, but it's the difference between the feature being usable and not.
**Shareable:** yes — the same document in Google Docs before and after: literal `# Heading` / `**bold**` versus rendered headings, real bold, and a table.
**Tags:** #integration #zapier #bugfix
_2 files changed, 199 insertions(+) · branch `drive-markdown-formatting`_
status: enriched

## 2026-09-06 10:23 · voice-capture · 09a171a
**What:** Added one index page for the dictation app's design prototypes: every prototype — capsule states, background treatments, the main window, the capture flow — listed and grouped in one place, with the ability to archive superseded versions and filter to just the current set. It's now what loads by default at `/prototype/`.
**Why it matters:** There were half a dozen loose prototype files and no map; finding "the latest main-window direction" meant knowing filenames. This makes the set browsable and keeps old versions out of the way without deleting them. Purely internal scaffolding.
**Shareable:** no
**Tags:** #dx #ui
_3 files changed, 1289 insertions(+), 897 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-05 07:58 · assistantOS · a6b70ef
**What:** Dropped a redundant sentence from the empty-project state on the
kanban board — it used to explain that a `tickets/` folder gets created for
you, right above four columns already saying "No tickets" in plain sight.
**Why it matters:** Small copy trim, but it's the same instinct as the kanban
redesign a day earlier: once you actually look at a screen instead of just
shipping it, the redundant bits get obvious fast.
**Shareable:** no — too small to stand alone.
**Tags:** #polish #ui
_1 file changed, 6 deletions(-) · branch `main`_
status: enriched

## 2026-09-04 23:58 · assistantOS · 388712a
**What:** Cleaned up the small text labels on the Social build-log cards
("Why it matters", "Shareable", tags, day headings) so they use the exact
same small-caps label style as the kanban board cards from earlier today,
instead of a handful of slightly-different one-off sizes and weights.
**Why it matters:** A follow-up to the kanban redesign — once one part of the
app got a real design-token pass, the mismatched sibling right next to it in
the nav became obvious. Small, but this is the kind of detail that decides
whether an app feels like one considered thing or several screens bolted
together.
**Shareable:** no — too small a diff to carry a post on its own; worth folding
into the kanban before/after post as a "and the sibling screen too" aside.
**Tags:** #polish #ui #design
_1 file changed, 5 insertions(+), 5 deletions(-) · branch `main`_
status: enriched

## 2026-09-04 23:42 · assistantOS · 093445c
**What:** Redesigned the Projects kanban board and ticket cards to look like a
real product instead of a functional prototype — clear swim lanes for each
column, colored priority dots, tidier spacing, and PR references that are now
actual clickable links instead of static text.
**Why it matters:** This is the board I actually use to track my own tickets,
and it looked like a wireframe. Matched it against two reference screenshots
of a polished SaaS kanban, but reused this app's own existing design tokens
rather than importing new colors or components — so the whole app still feels
like one system. Also caught and fixed a real keyboard bug along the way: the
new PR link (and the pre-existing run/delete buttons) would get hijacked by
the card's own click handler when activated with Enter instead of a mouse.
**Shareable:** yes — before/after of the kanban board, plus a close-up of one
card showing the priority dot + PR link.
**Tags:** #polish #ui #design #bugfix
_1 file changed, 79 insertions(+), 29 deletions(-) · branch `main`_
status: enriched

## 2026-08-31 17:47 · assistantOS · 50f4e86
**What:** Added a Social view inside the app itself that shows this very
build log — grouped by day, flagging entries still waiting to be enriched —
instead of having to open the raw markdown file to see what's been shipped.
**Why it matters:** The whole point of this log is to lower the friction of
remembering what I built well enough to post about it; making it visible
inside the app removes the last bit of friction (opening a separate file) and
makes half-finished stub entries visible so they don't just pile up unseen.
**Shareable:** no — this is tooling for writing about the other tools, not
something a reader outside this workflow would care about on its own.
**Tags:** #dx #infra #ui
_6 files changed, 517 insertions(+), 5 deletions(-) · branch `main`_
status: enriched

## 2026-08-31 13:46 · Skills · fd19891
**What:** Taught the build-log system to clear its whole backlog, not just the
latest entry. The automation drops a rough one-line "stub" after every commit
and I (well, the assistant) turn each into a real write-up — but stubs from
unattended runs or closed sessions were piling up untouched. Now any time the
system runs, it works through every unfinished stub oldest-first.
**Why it matters:** Second fix in a day to a thing I built yesterday. The
capture half was solid; the "turn it into something readable" half only fired
for whatever I'd just committed, so a gap of a few days meant a wall of raw
stubs to slog through later. Small change, but it's the difference between a
log that's always current and one that's a chore. Building-in-public tools
have to survive your actual habits, not your intended ones.
**Shareable:** no — too incremental on its own; fold into a broader "I'm
building a tool to make myself post more" thread if that ever gets written.
**Tags:** #dx #infra #building-in-public
_2 files changed, 15 insertions(+), 6 deletions(-) · branch `main`_
status: enriched

## 2026-08-31 09:18 · assistantOS · 7567265, e0354c0
**What:** Finished a pass giving the whole app one consistent motion language —
seven screens' worth of open/close, hover, and load-in animations built from a
shared set of timing/easing tokens instead of ad-hoc values scattered around.
The last piece was the file viewer: toggling in and out of edit mode now
replays the panel's own open animation so the swap reads as "the document
reopened," and closing plays that entrance in reverse at a quicker pace,
because dismissing something shouldn't feel as heavy as summoning it.
**Why it matters:** Motion is the thing that most separates an app that feels
considered from one that feels like a stack of forms. Doing it as a token
system rather than one-off transitions means the next new screen inherits the
feel for free, and there's a written `MOTION.md` so I'm not re-deciding
durations every time. Also a nice reminder that "done" is rarely done — the
close animation needed a watchdog for the case where a browser extension
strips animations without tripping the reduced-motion flag, or the close
button would silently stop working.
**Shareable:** yes — short screen recording of the file viewer opening,
toggling to edit mode, and closing; plus the `MOTION.md` token table.
**Tags:** #polish #ui #motion #design-system
_files across two commits: 8 changed (token cleanup) + 4 changed, 322 insertions — MOTION.md, file-viewer-sheet.tsx, motion.ts, index.css · branch `main`_
status: enriched

## 2026-08-31 08:24 · Skills · 48bccd6
**What:** Fixed a blind spot in the automation that logs my work: when I commit
with a one-liner like `cd other-project && git commit`, the session's working
directory never actually changes, so the logger was looking at the wrong repo
and silently skipping the commit. It now also scans all my project folders for
whichever one's latest commit just happened, and catches it.
**Why it matters:** I built this whole "log every commit so I can post about it
later" system a day ago, then immediately watched three of my own commits slip
through the cracks because of how I habitually type git commands. Kind of the
whole point of building in public — the tool meets real usage and the seams
show. This one's fixed; the log caught this very commit (the one adding the
fix) on the first try.
**Shareable:** yes — screenshot of the BUILD-LOG.md entry that logged its own
fix, side by side with the terminal showing the `cd … && git commit` that
triggered it.
**Tags:** #dx #infra #experiment #building-in-public
_3 files changed, 101 insertions(+), 50 deletions(-) · branch `main`_
status: enriched

## 2026-08-29 08:22 · cardio-tracking · 936aeb0
**What:** Rebuilt the route-drawing map screen in Move/Think — tap-to-plot
waypoints on a full-screen map with a distance readout that updates live,
controls that finally match the rest of the app's look, and a plain
read-only route viewer when you're just looking back at a past run instead
of editing it.
**Why it matters:** This screen had been a rough edge for a while — wrong
colors, markers invisible on light maps, and losing the app's own nav bar
after backing out of it. It now matches the app's actual design language
(same circular buttons as every other detail screen, same dot style as the
mood slider) and the route line/markers automatically flip black or white
so they're always visible against the map, in light or dark mode.
**Shareable:** yes — before/after of the route editor (purple line on dark
map vs. black line on light map), the floating controls close-up, and the
new read-only full-screen route view.
**Tags:** #polish #ui #bugfix
_9 files changed, 271 insertions(+), 127 deletions(-) · branch `main`_
status: enriched
