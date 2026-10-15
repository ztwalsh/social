# Automations dashboard — shot list

Blur zap names, email addresses, Slack text and any run input/output first: it's work data.

1. **Overview grid.** The Automations page with the stat row (Watching / Healthy / Need attention / Runs · 24h) and the health cards. Ideally one card showing a red "Failing" or amber "Gone quiet" pill next to green "Healthy" ones.
2. **"Choose zaps" picker.** The dialog listing only my own zaps with checkboxes, to show "only zaps I own, only zaps I choose".
3. **Detail page, top half.** Title with health pill, the four stat tiles, and the "Last 60 runs" timeline (bar height = duration, red dot = failure).
4. **30-day chart.** The "Last 30 days" card with a day hovered, so the header readout shows that day's numbers.
5. **Run panel.** A run opened in the side sheet; best if it's a failed one showing the error and stack trace (blur the payload).
6. **The Slack DM.** The alert landing on my phone from Zapier's bot, and the follow-up "recovered" message if I can catch one. The "Send test" button on the overview produces a harmless one on demand.
7. **Optional before/after.** Light vs dark mode of the detail page.
