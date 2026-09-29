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

## 2026-09-29 17:05 · harps-website + voice-capture · 8fe361b · ccc7103
**What:** Harps downloads now come from GitHub Releases instead of a file checked into the website's code. The site's Download buttons point at "latest release", and the app's release process now publishes each new version as a proper GitHub release with its notes — the first one, 0.4.4, is up.
**Why it matters:** Every release used to add another 1.6 MB copy of the app to the website's repository forever. Now releases are versioned, have their own page and notes, and the site automatically serves whichever is newest. Old download links still work.
**Shareable:** no — plumbing, though the public release page is a nice thing to link when announcing the next version
**Tags:** #release #github #harps #infra
_9 files changed, 51 insertions(+), 17 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 17:01 · harps-website · 81c0466
**What:** The animated hero on getharps.app (the drifting particles and the looping voice-capture demo) now stops when you scroll past it or switch tabs, and picks up exactly where it left off when you come back.
**Why it matters:** Both animations were running forever in the background, eating CPU and battery on a page most people scroll straight past — on laptops, which is the entire audience for a Mac app. The subtle part: simply pausing the demo would have made it jump ahead and break when resumed, so its internal clock pauses too.
**Shareable:** maybe — a short "your hero animation is probably still running after you scroll past it" tip, with the before/after CPU numbers
**Tags:** #perf #animation #harps #web
_5 files changed, 72 insertions(+), 7 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 16:51 · harps-website · 8f3e8d9
**What:** Switched getharps.app's fonts to the compressed web format, cutting them from 133 KB to 56 KB, and told the browser to show text immediately and fetch the two most-used weights first. Rendering is pixel-identical to before.
**Why it matters:** Faster first paint, no invisible-text flash while fonts load. Standard web hygiene — not post material on its own.
**Shareable:** no
**Tags:** #perf #fonts #harps #web
_13 files changed, 26 insertions(+), 6 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 15:13 · harps-website · b282f52 · 463aac2
**What:** Added automatic style checks to the Harps site: a linter that rejects any color, font size or animation curve that isn't one of the site's design tokens, and a formatter for the HTML. This was the first change to go through the new AI code-reviewer, and it failed my work twice before passing — first because the formatter would have rewritten files it was told to leave alone, then because it would have silently deleted the explanatory comments at the top of ten components.
**Why it matters:** The design tokens from yesterday are now enforced by a machine, not memory. And the reviewer earned its keep immediately: both catches were things I'd have shipped. The one-time formatting pass was verified pixel-for-pixel — zero pixels changed on any page.
**Shareable:** yes — pairs with the code-reviewer post: "its first gated ticket, it failed me twice, both times correctly"
**Tags:** #tooling #linting #ai-tools #code-review #harps
_8 files changed, 1852 insertions(+), 40 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 15:11 · zapier-gallery · 57e8d6f
**What:** Add tickets for remaining Okta and screenshot-bypass work
**Why it matters:** _(stub — enrich me)_
**Shareable:** ?
**Tags:**
_3 files changed, 124 insertions(+) · branch `main`_
status: stub

## 2026-09-29 15:02 · harps-website + Skills · 9ecba96 · 00a89d3
**What:** Built a reusable AI code-reviewer that judges changes only against a project's own written rules (its design doc), not generic best practices — saved as a universal tool in my public Skills repo that can be dropped into any project, and installed first on the Harps site. To prove it worked, I fed it a deliberately sloppy change (it failed it, citing every broken rule) and then one of my own real commits from an hour earlier — which it also failed, correctly: the design doc I'd just written made a claim the site didn't back up.
**Why it matters:** The reviewer's very first real review caught a mistake I'd shipped and missed. A reviewer that only cites rules a human wrote down is one you can actually trust to block things — and now every future change to the site gets checked before it lands.
**Shareable:** yes — "my new AI reviewer's first real catch was my own commit" angle
**Tags:** #ai-tools #code-review #claude-code #harps #workflow
_11 files changed, 122 insertions(+), 20 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 14:49 · harps-website · 911e890
**What:** Settled three small design questions the new design doc had flagged on getharps.app: the home page's sections and footer now line up exactly with the header (they'd been sitting 8px off), two color tokens that were secretly the same color became one, and the accent color keeps its "live" name on purpose.
**Why it matters:** Writing the design doc down is what surfaced the misalignment — an 8px drift nobody had noticed. Small polish; a nice footnote to the design-doc story rather than its own post.
**Shareable:** no
**Tags:** #polish #design-systems #harps
_7 files changed, 27 insertions(+), 31 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 10:03 · harps-website · cfc2dee
**What:** Rewrote the Harps website's design doc to describe the site as it actually is — it had still been describing an earlier light, red-accented version. It now covers the real palette, the new type/motion/layout tokens, every component, the coding rules learned the hard way this week, and a step-by-step recipe for adding a page (tested by building a throwaway page from it).
**Why it matters:** This doc is what future work — including automated reviewers — gets checked against. A design doc that describes a site that no longer exists is worse than none. Internal, not post material on its own.
**Shareable:** no
**Tags:** #docs #design-systems #harps
_2 files changed, 217 insertions(+), 67 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 09:43 · harps-website · 0560c60
**What:** Gave getharps.app a real design-token system: a single type scale, named motion curves and durations, and shared layout widths and section spacing, with every component pointing at them. Along the way, 21 different font sizes in use on a three-page site collapsed to 13 — most of the extras were half-pixel near-duplicates like 13 vs 13.5.
**Why it matters:** "21 font sizes on a 3-page site" is a relatable kind of drift — nobody chose it, it just accumulated one tweak at a time. Now a new page picks from a short list instead of eyeballing a number.
**Shareable:** yes — "counted the font sizes on my tiny site: 21" angle
**Tags:** #design-systems #tokens #harps #web #css
_13 files changed, 116 insertions(+), 64 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 09:38 · harps-website · 758be6f
**What:** The Harps changelog page now has its release notes baked into the page when the site is built, instead of loading them with JavaScript after the page opens.
**Why it matters:** The page no longer flashes empty, search engines can actually read the release notes, and there's no "couldn't load" failure state. Small follow-on to the Astro move — plumbing, not a post on its own.
**Shareable:** no
**Tags:** #astro #harps #web #seo
_2 files changed, 51 insertions(+), 57 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 09:16 · harps-website · f8aa199 · 144276e
**What:** Moved getharps.app from hand-copied HTML files onto Astro: every page now shares one layout for its head, analytics, header and footer, so a new page is a small file instead of a copy-paste of the last one. The home page followed: its hero animation, feature grid, stepper, and pricing card are now reusable components, and the Download button carries its own click tracking. Verified with a pixel-by-pixel screenshot diff against the live site — which turned up a real bug: headings on the inner pages had been stuck a few pixels short of where their entrance animation should land, on the live site, for everyone.
**Why it matters:** The site only has three pages and they'd already drifted into three slightly different copies of the same code. Fixing structure before adding more pages is the cheap moment. The pixel diff catching a live bug nobody had noticed is the fun part.
**Shareable:** yes — "screenshot-diffed my own site during a migration and found a bug that was already live" angle
**Tags:** #astro #refactor #harps #web #testing
_35 files changed, 4499 insertions(+), 327 deletions(-) · branch `main`_
status: enriched

## 2026-09-29 08:57 · harps-website · 46cd4cc
**What:** Swapped getharps.app onto a brand-new Google Analytics tag after the previous one turned out to be dead on Google's side — Google refused to serve its script (404) even though it happily serves one for made-up IDs. Visits are now confirmed reaching GA.
**Why it matters:** A day of "No data received" had nothing to do with the site; the tag ID itself was broken upstream. Mostly plumbing, though the debugging trick (compare the real ID against a fake one) is a mildly useful tip.
**Shareable:** no
**Tags:** #analytics #debugging #harps
_3 files changed, 6 insertions(+), 6 deletions(-) · branch `main`_
status: enriched

## 2026-09-28 22:48 · harps-website · abec0c5
**What:** The two "Download for Mac" buttons on getharps.app now report clicks to Google Analytics, each labeled with where it sits (header vs. pricing section), so downloads can be counted and the two buttons compared.
**Why it matters:** GA's automatic download tracking doesn't recognize .dmg files, so until now there was no way to know how many people actually downloaded the app from the site. Small instrumentation, but it's the first real signal on whether the site converts.
**Shareable:** no
**Tags:** #analytics #harps #instrumentation
_2 files changed, 12 insertions(+), 2 deletions(-) · branch `main`_
status: enriched

## 2026-09-28 22:46 · voice-capture · b167656
**What:** Harps' Settings and Transforms pages now group their rows into bordered, iOS-style card sections — Settings splits into Dictation / Storage / General instead of one long flat list — matching the grouped-list look of the cardio-tracking sibling app, using a plain hairline border with no background or shadow change.
**Why it matters:** Settings had quietly grown to a dozen-plus rows in one undifferentiated column; grouping them is the difference between a settings screen that looks native to macOS and one that reads as a form. Also a good real-time example of iterating live with feedback — an early pass added a background wash and drop shadow that changed the whole page's tone, and got reverted back down to just borders once that looked wrong running in the actual app.
**Shareable:** yes — before/after of the Settings page (flat list vs. the three bordered groups).
**Tags:** #polish #ui #macos
_3 files changed, 143 insertions(+), 49 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-28 22:44 · cardio-tracking-website · 647bad8
**What:** Hooked movethink.app up to Google Analytics, and added a short "This website" section to the privacy policy saying that the site (not the app) counts visits, and that none of it is tied to an account.
**Why it matters:** First time the Move/Think landing page can show whether anyone is actually visiting ahead of launch. Doing the disclosure in the same commit keeps the "the app doesn't track you" promise honest, since the tracking stays on the marketing site.
**Shareable:** no (plumbing; pairs with the harps GA cleanup from the same night if there's ever an "analytics housekeeping" post)
**Tags:** #analytics #privacy #movethink #web
_2 files changed, 28 insertions(+), 1 deletion(-) · branch `main`_
status: enriched

## 2026-09-28 22:38 · harps-website · 9ddd20e
**What:** First cleanup pass on getharps.app after a full code audit: fixed a privacy contact address that bounced and a footer linking the wrong domain, added a favicon and link-preview tags, and stopped old prototypes and internal docs from being publicly viewable. Also wrote a 10-ticket plan to move the site onto Astro with shared layouts so new pages stop being copy-paste.
**Why it matters:** The audit turned up real bugs hiding in a "finished" site — anyone emailing about privacy was getting a bounce. The bigger story is the plan: a three-page static site had already drifted into three slightly different copies of the same header and animations, which is the moment to fix structure before adding more pages.
**Shareable:** yes — "I audited my own tiny marketing site and found a dead contact email" angle; capture the ticket list and before/after of the browser tab favicon
**Tags:** #audit #cleanup #harps #web #astro
_15 files changed, 237 insertions(+), 5 deletions(-) · branch `main`_
status: enriched

## 2026-09-28 22:28 · harps-website · 99e65b7
**What:** Moved getharps.app's Google Analytics tag over to a fresh, dedicated Harps property, so visits to the site now show up alongside the rest of Zachary's GA accounts instead of in a stray property nobody could find.
**Why it matters:** Housekeeping — the old tag pointed at a property of unknown whereabouts, so site traffic was effectively invisible. Minor plumbing, not post material on its own.
**Shareable:** no
**Tags:** #analytics #housekeeping #harps
_3 files changed, 6 insertions(+), 6 deletions(-) · branch `main`_
status: enriched

## 2026-09-28 22:00 · zapier-gallery · 5559db4
**What:** Replaced the internal prototype gallery's "just type your name" placeholder login with real Okta sign-in, and now requires it to submit a prototype or post an activity update — both now attribute to the actual signed-in person instead of a free-text name, and the "Mine" filter (previously a permanent disabled placeholder) actually works.
**Why it matters:** Closes the obvious hole in a shared internal tool — anyone could previously post as anyone by just typing a different name. Real auth is what makes "Mine" and attribution trustworthy.
**Shareable:** no — internal Zapier tooling, not for a public audience.
**Tags:** #infra #integration #zapier
_15 files changed, 195 insertions(+), 82 deletions(-) · branch `main`_
status: enriched

## 2026-09-24 19:24 · zapier-gallery · dc44ad5
**What:** Fixed screenshot capture silently failing in production on Vercel, and pointed the companion submit-to-gallery CLI at the real deployed gallery URL by default.
**Why it matters:** A serverless-only bug — `@sparticuz/chromium` loads its binary from disk at runtime, so Next's bundler was dropping it from the deployed bundle even though everything worked locally. The kind of failure that only shows up once something's actually live.
**Shareable:** no — infra bugfix on an internal tool.
**Tags:** #bugfix #infra #zapier
_3 files changed, 18 insertions(+), 13 deletions(-) · branch `main`_
status: enriched

## 2026-09-24 19:18 · zapier-gallery · 722b4ad
**What:** Made the build script explicitly run `prisma generate` instead of relying on it firing automatically after install.
**Why it matters:** Vercel skips postinstall scripts for packages it doesn't already trust, so the Prisma client was silently never generated and the build failed on a type check with no obvious cause. One-line fix once found.
**Shareable:** no — build plumbing.
**Tags:** #bugfix #infra #zapier
_1 file changed, 1 insertion(+), 1 deletion(-) · branch `main`_
status: enriched

## 2026-09-24 19:09 · zapier-gallery · ffcd9e3, 71a0fb9
**What:** First commit of a new internal tool: a gallery for browsing Zapier prototype apps, submitted either through the site or a companion CLI/skill that posts straight from another repo.
**Why it matters:** Gives scattered internal prototypes one shared, browsable home instead of living only in whichever repo built them.
**Shareable:** no — internal Zapier tooling.
**Tags:** #new-feature #infra #zapier
_71 files changed, 11084 insertions(+) · branch `main`_
status: enriched

## 2026-09-24 12:03 · harps-website · 8894e4e
**What:** Published the v0.4.4 changelog entry and updated the downloadable DMG on getharps.app.
**Why it matters:** The changelog page is the paper trail for what "0.4.4" actually means to someone who isn't reading commits — see the paired voice-capture entry (`fbe222a`, same night) for the real fix.
**Shareable:** no — the website side is just publishing; the fix itself is the story.
**Tags:** #harps #dx
_2 files changed, 7 insertions(+) · branch `main`_
status: enriched

## 2026-09-24 12:02 · voice-capture · fbe222a
**What:** Fixed the real source of slow transcription in Harps: the on-device cleanup step (stripping filler words, tightening phrasing) now reuses one warmed-up AI session for the app's whole lifetime instead of spinning up a brand-new one on every single dictation.
**Why it matters:** This is the second release in a row chasing the same root cause from a different angle (v0.4.3 fixed the speech model itself; this fixes the follow-up cleanup pass) — the kind of fix that doesn't show up as a new feature but is exactly what "feels fast" is made of.
**Shareable:** no — a latency fix has no visual to show; would read better as a line in a "Harps got noticeably snappier" recap than its own post.
**Tags:** #perf #bugfix #ai #harps
_3 files changed, 51 insertions(+), 5 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-24 11:31 · harps-website · 8cb2f8e
**What:** Published the v0.4.3 changelog entry and updated the downloadable DMG.
**Why it matters:** Pairs with the same-day voice-capture fix (`0333d85`) — see that entry for what actually changed.
**Shareable:** no.
**Tags:** #harps #dx
_2 files changed, 7 insertions(+) · branch `main`_
status: enriched

## 2026-09-24 11:31 · voice-capture · 0333d85
**What:** Transcription is noticeably faster in Harps now — the on-device speech model stays loaded for the app's entire session instead of being torn down and rebuilt before every single capture.
**Why it matters:** "Hold a key, speak, see text" only feels instant if nothing has to warm up in between; this removes a reload that was happening on literally every dictation.
**Shareable:** no — a latency win, nothing new to look at.
**Tags:** #perf #harps
_2 files changed, 17 insertions(+), 2 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-23 10:14 · ztwalsh.com · c810a2f
**What:** Rebuilt my personal site's whole look: black-and-white instead of
green-and-gold, and the entire page now renders through a real WebGL CRT
shader — scanlines, bloom, RGB shift — with a click to invert between a dark
and light "tube." Also added Solid State, a drag-to-spin point-cloud toy that
morphs between sphere, cube, and pyramid, to the experiments list.
**Why it matters:** This started as two throwaway Claude artifact prototypes
that got good enough to ship for real — mirroring the actual DOM onto a canvas
and running it through a genuine CRT fragment shader, not a CSS filter doing a
vague scanline impression. The invert toggle plays a little power-cycle
animation, which is the kind of detail that makes a personal site feel like a
piece of software instead of a brochure.
**Shareable:** yes — screen recording of the invert toggle's power-cycle
animation, plus the Solid State toy being dragged/spun on the experiments page.
**Tags:** #new-feature #ui #design #experiment
_7 files changed, 1136 insertions(+), 353 deletions(-) · branch `main`_
status: enriched

## 2026-09-21 17:07 · harps-website · 551be5f
**What:** Published the v0.4.2 changelog entry and updated the downloadable DMG.
**Why it matters:** Pairs with the same-day voice-capture fix (`d98224b`) — see that entry for the actual changes.
**Shareable:** no.
**Tags:** #harps #dx
_2 files changed, 8 insertions(+) · branch `main`_
status: enriched

## 2026-09-21 17:07 · voice-capture · d98224b
**What:** Fixed a crash that could hit shortly after finishing a recording, most noticeable on longer captures, and gave the Overview page's stat cards a red down-arrow when a number has dropped versus last week instead of showing nothing next to "vs last week."
**Why it matters:** A crash right after you finish speaking is about the worst possible moment for one — it's exactly when you're about to paste the result somewhere. The stat-card fix is small but makes the dashboard actually readable at a glance instead of only half-telling the story.
**Shareable:** yes — the stat cards showing the new red down-indicator next to a dropped number.
**Tags:** #bugfix #ui #harps
_4 files changed, 49 insertions(+), 22 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-19 12:11 · harps-website · b345458, 1b8c288
**What:** Two quick rewrites of the one-line intro sentence at the top of the Harps changelog page, minutes apart, landing on "Keep up with Harps. There's always something new in the works."
**Why it matters:** Just copy-tightening — the kind of pass where you write a line, read it back, and immediately try again.
**Shareable:** no — too small to stand alone.
**Tags:** #polish #content #harps
_1 file changed, 1 insertion(+), 1 deletion(-) · branch `main`_
status: enriched

## 2026-09-19 12:03 · harps-website · ef452cc
**What:** Published the v0.4.1 changelog entry and updated the downloadable DMG.
**Why it matters:** Pairs with the same-day voice-capture polish pass (`6ad904e`) — see that entry for what changed.
**Shareable:** no.
**Tags:** #harps #dx
_2 files changed, 10 insertions(+) · branch `main`_
status: enriched

## 2026-09-19 12:02 · voice-capture · 6ad904e
**What:** Switching between Today and other days in Harps' sidebar now animates instead of snapping instantly, added a Cancel button next to Save in the Transforms editor, gave the text area more breathing room, fixed wrapped bulleted/numbered list lines falling back to the left margin instead of indenting correctly, and polished the shape of the recent-captures refresh button.
**Why it matters:** A pure polish pass — nothing new to do, everything a little more pleasant to look at and use, especially the day-switch animation and the list-indent fix, which was the kind of small "off" detail that's easy to walk past until it's fixed.
**Shareable:** yes — the day-switch animation, and a wrapped list before/after (falling to the margin vs. indenting correctly).
**Tags:** #polish #ui #motion #harps
_5 files changed, 67 insertions(+), 6 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-19 08:10 · harps-website · 8d5414e
**What:** Published the v0.4.0 changelog entry and updated the downloadable DMG.
**Why it matters:** Pairs with the same-day voice-capture release (`d3e8aca`) — see that entry for what changed.
**Shareable:** no.
**Tags:** #harps #dx
_2 files changed, 10 insertions(+) · branch `main`_
status: enriched

## 2026-09-19 08:10 · voice-capture · d3e8aca
**What:** Added a manual refresh button (on Overview and Today's Transcripts) to pull in captures recorded since the window was last opened, fixed a crash that could happen when starting a new capture while the previous one was still transcribing, made deleting a transform ask for confirmation instead of deleting immediately, and gave opening a transform a smooth transition instead of a hard cut.
**Why it matters:** The refresh button and delete confirmation are both "I actually hit this while using my own app" fixes — a background recording's captures not showing up until something else nudged the view, and a one-click-undoable delete on something you spent time writing, are exactly the rough edges that make an app feel unfinished.
**Shareable:** yes — the refresh button spinning as it pulls in new captures, and the delete-confirmation step on a transform.
**Tags:** #new-feature #bugfix #ui #harps
_8 files changed, 199 insertions(+), 63 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-19 07:20 · harps-website · 968edc3
**What:** Moved an old particle-background experiment out of the site's root and into its playground folder, with a link from the playground index.
**Why it matters:** Housekeeping — keeping one-off visual experiments out of the way of the real site pages.
**Shareable:** no.
**Tags:** #dx #housekeeping
_2 files changed, 5 insertions(+) · branch `main`_
status: enriched

## 2026-09-19 07:17 · harps-website · 153f4f5
**What:** Published the v0.3.0 changelog entry and updated the downloadable DMG.
**Why it matters:** Pairs with the same-day voice-capture release (`08133d5`) — see that entry for what changed.
**Shareable:** no.
**Tags:** #harps #dx
_2 files changed, 10 insertions(+) · branch `main`_
status: enriched

## 2026-09-19 07:16 · voice-capture · 08133d5
**What:** Gave Harps' Transforms a real editor — a formatting toolbar (headings, bold, italic, code, lists) with both a clean Rich Text view and a raw Markdown view that stay in sync — made transcription noticeably faster by loading the speech model once at launch instead of rebuilding it before every capture, and fixed the transcribing indicator's animated dots plus the capture timer wrapping onto two lines on longer recordings.
**Why it matters:** Transforms went from a plain textarea to an actual editor, which is the difference between writing a clean-up rule once and fighting raw Markdown syntax every time you tweak one.
**Shareable:** yes — the Transforms rich-text toolbar, switching between Rich Text and Markdown views on the same rule.
**Tags:** #new-feature #ui #ai #harps
_7 files changed, 824 insertions(+), 43 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-19 06:49 · ticket-home-hero-generating-state · 9185f1c
**What:** Cold-start on cardio-tracking's Home hero (no cached headline yet) now shows a shimmer-pulsed skeleton with honest "generating" copy for the headline and theme chips, instead of a static fallback line dressed up as a finished insight. Warm starts still show cached content instantly, and generated headlines now actually get cached so warm starts stay reachable across launches.
**Why it matters:** A static placeholder that looks like a real insight is a small lie — this makes "the app is thinking" visibly true instead of quietly faking a finished thought while the model runs.
**Shareable:** yes — the shimmer skeleton state, side by side with the instant warm-start version.
**Tags:** #ui #polish #ai
_1 file changed, 108 insertions(+), 14 deletions(-) · branch `worktree-ticket-home-hero-generating-state`_
status: enriched

## 2026-09-18 16:38 · ticket-home-hero-period-comparison · 8665241
**What:** Cardio-tracking's Home hero headline can now name a real month-over-month comparison ("more runs than last month," etc.) when there's enough data in the prior window — grounded only in totals and mood mix, never a specific theme or note-level claim about the previous period, and never raw numbers in the headline text itself.
**Why it matters:** A single-window summary ("you ran 5 times") is less interesting than one that knows whether that's up or down from before — this is what turns the hero into something closer to an actual insight instead of a fact restated.
**Shareable:** yes — the before/after headline copy: single-window summary vs. a real comparison line.
**Tags:** #new-feature #ai
_2 files changed, 108 insertions(+), 7 deletions(-) · branch `worktree-ticket-home-hero-period-comparison`_
status: enriched

## 2026-09-18 16:23 · cardio-tracking · f5608b3
**What:** Wrote three tickets scoping the next round of Home hero work: a freshness/cache-invalidation fix, the month-over-month comparison, and the honest generating-state skeleton — the three that shipped over the following day (see the entries above and below).
**Why it matters:** Planning, not a feature — the paper trail for how one ticket queue became three shipped fixes in under 24 hours.
**Shareable:** no.
**Tags:** #dx #infra
_3 files changed, 238 insertions(+) · branch `main-sync`_
status: enriched

## 2026-09-18 16:22 · queue-main · 909a0dc
**What:** Fixed the ticket queue's own bookkeeping — a ticket had gotten erroneously re-locked, which wiped its review status and PR link; restored both.
**Why it matters:** Internal tooling housekeeping — keeping the ticket queue's own state honest so it doesn't lose track of work that's actually done.
**Shareable:** no.
**Tags:** #dx #infra
_1 file changed, 3 insertions(+), 1 deletion(-) · branch `queue-main-snapshot`_
status: enriched

## 2026-09-18 14:23 · ticket-home-hero-freshness-cache-invalidation · b32b57e, fb34328
**What:** Fixed cardio-tracking's Home hero cache so it regenerates the headline/theme summary whenever runs, notes, or moods change inside the current rolling window — not only when the calendar month rolls over, which was the only thing that used to bust the cache.
**Why it matters:** Before this, logging a new run (or editing an old one's notes) didn't change the hero's summary at all until the next month started — the headline could sit stale, quietly describing data that had since changed. Two commits on the same ticket: an initial fingerprint-based fix, then a same-day refinement to how that fingerprint is computed.
**Shareable:** no — a correctness/cache fix with nothing new to look at, though it's the reason the comparison and generating-state features above actually stay accurate.
**Tags:** #bugfix #ai
_2 commits, ~62 insertions / 19 deletions across InsightRange.swift · branch `worktree-ticket-home-hero-freshness-cache-invalidation`_
status: enriched

## 2026-09-17 22:54 · harps-website · 22c3191
**What:** Published the v0.2.0 changelog entry and updated the downloadable DMG.
**Why it matters:** Pairs with the same-day voice-capture release (`370f3b5`) — see that entry for what changed. This is the release that introduced Transforms, so it's the more interesting half of the pair.
**Shareable:** no — website-side publishing only.
**Tags:** #harps #dx
_2 files changed, 11 insertions(+) · branch `main`_
status: enriched

## 2026-09-17 22:53 · voice-capture · 370f3b5
**What:** Added Transforms to Harps — on-device text clean-up rules that apply automatically as you dictate, shipping with a General Clean-up default and support for writing your own — plus a hotkey mode setting (hold-to-record or press-to-toggle), a fix so clicking the Dock/Applications icon reliably opens the dashboard and switches the menu bar even across multiple displays and Spaces, a freely resizable sidebar with icons, and a round of copy/delete interaction polish (hover states, a copy confirmation, a Cancel/Delete step before deleting a capture).
**Why it matters:** Transforms is the headline feature of this release — it's the difference between "transcribe exactly what I said" and "transcribe what I meant," entirely on-device. Everything else in this release is the app catching up to feeling reliable around it (opening reliably from the Dock, a sidebar that fits your screen).
**Shareable:** yes — Transforms actually cleaning up a dictated sentence (filler words removed, phrasing tightened) as the headline moment, plus the resizable sidebar.
**Tags:** #new-feature #ui #harps
_41 files changed, 2544 insertions(+), 85 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-17 21:36 · harps-website · 10ef374, 0287d77
**What:** Added a real changelog page to getharps.app and moved the Privacy/Changelog links out of the header and into the footer.
**Why it matters:** Gives the site a public paper trail of what's shipped, matching the version-bump cadence the app itself was already on. (Two identical SHAs from the same commit attempt — merged into one entry.)
**Shareable:** no — site plumbing.
**Tags:** #new-feature #harps #web
_3 files changed, 178 insertions(+), 1 deletion(-) · branch `main`_
status: enriched

## 2026-09-17 15:30 · assistant · c771b9f
**What:** Imported meeting notes from a Growth Zone Leads AMA into the assistant project.
**Why it matters:** Housekeeping — feeding the assistant real meeting context to work from, not a feature.
**Shareable:** no.
**Tags:** #housekeeping
_1 file changed, 269 insertions(+) · branch `main`_ _(reconstructed from commit metadata — repo/SHA not locally reachable)_
status: enriched

## 2026-09-17 13:47 · assistant · 81c2d66
**What:** Imported four more meeting transcripts (three 1-1s and a Post Build All-Hands Q&A) into the assistant project.
**Why it matters:** Housekeeping — same as the entry above.
**Shareable:** no.
**Tags:** #housekeeping
_4 files changed, 1524 insertions(+) · branch `main`_ _(reconstructed from commit metadata — repo/SHA not locally reachable)_
status: enriched

## 2026-09-16 22:19 · harps-website · b75cbac
**What:** Swapped the site's downloadable DMG for the first public build — the one with Harps' real icon and a designed installer background, matching changelog v0.1.0 ("First public build of the Harps DMG, with the new icon and installer background").
**Why it matters:** This is the DMG a stranger actually double-clicks — the difference between a generic installer window and one that looks like it belongs to a finished app.
**Shareable:** yes — the DMG installer window with the real icon and background art.
**Tags:** #polish #ui #harps
_1 file changed, 0 insertions(+), 0 deletions(-) · branch `main`_
status: enriched

## 2026-09-16 22:14 · ztwalsh.com · bc563a3, e25711e
**What:** Swapped the personal site's icon set over to Hugeicons and moved Harps to the top of the experiments list.
**Why it matters:** Harps had become the thing actually worth leading with on the experiments page, and a consistent icon set is the kind of detail that makes a personal site's "experiments" list feel curated rather than accumulated. (Two identical SHAs — merged into one entry.)
**Shareable:** yes — before/after of the experiments list icons, plus Harps now at the top.
**Tags:** #polish #ui #design
_3 files changed, 39 insertions(+), 18 deletions(-) · branch `main`_
status: enriched

## 2026-09-16 14:37 · assistant · 6a84d1a
**What:** Imported eight more meeting transcripts (a skip 1-1, a Growth Zone merger AMA, a design/research roundtable) into the assistant project.
**Why it matters:** Housekeeping — same as the other meeting-note import entries this week.
**Shareable:** no.
**Tags:** #housekeeping
_8 files changed, 1966 insertions(+) · branch `main`_ _(reconstructed from commit metadata — repo/SHA not locally reachable)_
status: enriched

## 2026-09-13 21:47 · harps-website · f0ac4fe
**What:** Wired up Google Analytics on the marketing site and rewrote the privacy page's "This website" section, which had previously stated outright that there was no analytics on the site — now it accurately discloses what GA collects (cookies, standard visit data like pages viewed and device/browser type) and makes explicit that the actual Mac app is unaffected and still has zero telemetry or connection to Google.
**Why it matters:** The interesting part isn't the tracking snippet itself — it's the discipline of catching that adding analytics quietly made an existing privacy claim false, and fixing the claim in the same change instead of letting the site's stated privacy stance drift out of sync with what it actually does.
**Shareable:** no — infrastructure, and the actual interesting bit (a privacy page that keeps itself honest) is subtle enough to undersell in a screenshot.
**Tags:** #infra #privacy
_2 files changed, 23 insertions(+), 2 deletions(-) · branch `main`_
status: enriched

## 2026-09-13 15:34 · harps-website · b18e5a6
**What:** Bumped up the type size on the hero subhead, feature-card headings, and how-it-works step headings for clearer hierarchy, and simplified the pricing card — folded "Lifetime access" directly into the badge instead of repeating it as a separate heading, and updated the section headline to "Free for everyone."
**Why it matters:** A pass of the same instinct as the rest of this week's work on the site — once the bigger structural pieces (how-it-works section, pricing card, dark-only palette) were in place, the remaining gap was type feeling a size too small in a few spots.
**Shareable:** no — incremental type/copy tightening, not visually distinct enough to carry its own post; would read fine as an aside in a broader "here's the finished site" thread.
**Tags:** #polish #ui #design
_1 file changed, 10 insertions(+), 10 deletions(-) · branch `main`_
status: enriched

## 2026-09-13 11:52 · harps-website · d1ee1cb
**What:** Killed light mode on the marketing site entirely — the page now always renders the dark palette, no matter the visitor's system setting.
**Why it matters:** A straightforward call ("it looks better") but a real one: rather than maintaining two palettes that both need to look intentional, the site now commits to one. Cleaned up the code too — the capsule's shadow and the hero's ambient particle field no longer branch on `prefers-color-scheme`, since there's only one scheme now.
**Shareable:** no — a "we removed a feature" commit doesn't carry a post on its own; worth a passing line in a broader "here's the site" thread if one gets written.
**Tags:** #polish #ui #design
_2 files changed, 23 insertions(+), 54 deletions(-) · branch `main`_
status: enriched

## 2026-09-13 11:20 · harps-website · ea65c24
**What:** Built a real three-step "how it works" section for the homepage — capture, transcribe, review & tune — each step with its own tiny live mockup (a listening capsule, text assembling in a field, a mini activity/settings window), replacing a section that had sat there with just an unlabeled dashboard screenshot and nothing else. Also reworked the footer (simplified to just the brand mark and copyright, no link clutter), evened out and increased the spacing between every section, and gave the privacy page the same load-in/scroll-reveal motion the homepage already had.
**Why it matters:** The site had a "How it works" link in the nav that, until this, actually scrolled to the feature grid — there wasn't a real how-it-works section at all. This closes that gap with an actual walkthrough instead of a placeholder, and catches the privacy page up so it doesn't feel like a separate, unfinished corner of the site.
**Shareable:** yes — before/after of the old bare dashboard mockup vs. the new three-step stepper, plus a clip of each mini mockup animating (pulsing capsule, text typing in, the settings toggle).
**Tags:** #new-feature #ui #polish #motion
_5 files changed, 572 insertions(+), 60 deletions(-) · branch `main`_
status: enriched

## 2026-09-13 09:56 · harps-website · 717f48b
**What:** Fixed three icons in the feature grid that didn't match what they were labeling (a music note for "search," a hamburger menu for "works in any app," a lightning bolt for "push-to-talk"), removed a couple of unnecessary divider lines, and rebuilt the pricing section from a two-tier free/paid structure into a single "free during early access" card that hints at a future $5 one-time price without committing to a date.
**Why it matters:** The pricing rewrite solves a real problem: how do you launch free without training everyone to expect free forever? The card says exactly that — early access is free, and there'll be a one-time cost once it's ready to leave that phase — without overpromising specifics. Also caught a genuinely sneaky CSS bug along the way: a hover transition that looked correctly written but silently never applied, because a later, unrelated rule with equal specificity was fully overwriting the `transition` property on the same elements.
**Shareable:** yes — before/after of the pricing card (two-tier vs. single early-access card), and the icon swaps side by side with what they used to be.
**Tags:** #ui #polish #bugfix #pricing
_2 files changed, 33 insertions(+), 32 deletions(-) · branch `main`_
status: enriched

## 2026-09-13 09:39 · harps-website · 6116095
**What:** The homepage's "Download for Mac" buttons now point at a real, signed and notarized DMG instead of a dead `#download` anchor that went nowhere. Also carried forward a handful of smaller edits that had been sitting uncommitted locally — softer hero headline copy, smoother card hover easing, and a couple of unneeded section-divider lines removed.
**Why it matters:** This is the moment the site stopped being a mockup and started being able to actually convert a visitor — clicking Download used to be a dead end, now it's the real app.
**Shareable:** no — infrastructure/plumbing, nothing visually new to show; the fact that the button now works is more of a footnote in a "the site is live" post than its own.
**Tags:** #infra #bugfix
_2 files changed, 12 insertions(+), 18 deletions(-) · branch `main`_
status: enriched

## 2026-09-13 08:23 · harps-website · d01eb51
**What:** Promoted the hero's headline demo from a playground prototype to the real homepage: a text field and a capsule now swap places on the same line to show the product's actual loop — idle → listening → transcribing → the result drops into the field → dwells → deletes itself → loops. Rebuilt the crossfade so the capsule's inner content (dot, waveform, label, timer) fades out and back in on its own short delay, decoupled from the pill's own collapse/expand, so nothing ever looks squished mid-transition.
**Why it matters:** This is the first thing anyone sees on the site, and it went from a static screenshot to a live, looping demonstration of the actual product — a visitor watches the real capture-to-text loop before reading a single line of marketing copy.
**Shareable:** yes — screen capture of the full hero loop: field idle, capsule rising and listening, transcribing, text dropping into the field, then deleting and looping again.
**Tags:** #new-feature #ui #motion
_3 files changed, 525 insertions(+), 59 deletions(-) · branch `main`_
status: enriched

## 2026-09-12 19:37 · harps-website · 1beb0a9, 4f23ee1
**What:** Two small consistency fixes minutes apart: the accent color was still the original red in light mode even though dark mode had already switched to the Figma file's blue, so both modes were made to match — and the header picked up a touch more top padding so it doesn't feel cramped against the browser edge.
**Why it matters:** Housekeeping, not a feature — the kind of small mismatch that's invisible until you flip between light and dark and notice the accent color changed meaning halfway through.
**Shareable:** no — too small to stand alone.
**Tags:** #polish #ui
_2 files changed, 3 insertions(+), 3 deletions(-) · branch `main`_
status: enriched

## 2026-09-12 17:30 · harps-website · b193d6e
**What:** Added a `.gitignore` entry for the local Vercel project-link files so they stop showing up as untracked in every `git status`.
**Why it matters:** Pure housekeeping — keeps the repo clean, nothing a reader would care about.
**Shareable:** no
**Tags:** #housekeeping #dx
_1 file changed, 2 insertions(+) · branch `main`_
status: enriched

## 2026-09-12 17:17 · voice-capture · f0d585f
**What:** Replaced every system icon in the app with a real icon set pulled by hand from Central Icons, added search filters and an auto-delete setting for old transcripts, gave Document view a selection-anchored copy/delete toolbar, added a Feedback page that dogfoods the app's own dictation hotkey, and fixed a real bug where that hotkey silently did nothing while the app's own window was focused.
**Why it matters:** The hotkey fix is the one that actually matters to a user — "hold the hotkey to dictate" not working while inside the app's own window (e.g. typing feedback about the app) is exactly the kind of self-referential bug that's easy to miss and embarrassing to ship. Root cause was a one-line macOS gotcha: `addGlobalMonitorForEvents` explicitly never fires for a process's own windows. Everything else is the visual pass catching up to a real icon system instead of borrowed SF Symbols and hand-drawn shapes.
**Shareable:** yes — before/after of the icon set (SF Symbols vs. Central Icons), and a quick clip of dictating feedback into the app's own Feedback page.
**Tags:** #bugfix #ui #polish #new-feature
_20 files changed, 1912 insertions(+), 576 deletions(-) · branch `claude/mac-voice-capture-app-fdpi64`_
status: enriched

## 2026-09-12 17:17 · harps-website · 224fca2
**What:** Stood up a static marketing site for Harps, built straight from the app's own design system — same fonts (Geist/Geist Mono), same near-monochrome palette, plus a hero section with a capsule demo that cycles through the app's own states live.
**Why it matters:** _(reconstructed from commit metadata)_ Building the marketing site directly off the app's `design.md` rather than a fresh design pass means the site and the app can't visually drift apart — anyone who tries the site sees exactly the product they'd actually get.
**Shareable:** yes — the live-cycling capsule hero is the kind of thing that reads well as a short clip.
**Tags:** #new-feature #marketing #ui
_19 files changed, 2578 insertions(+) · branch `main`_
status: enriched

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
