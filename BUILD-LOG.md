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
