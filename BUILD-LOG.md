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
