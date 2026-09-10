# Shot list — voice-capture Phase 0 spikes

For the build-log entry `910a3bc, 63b6c3c` (2026-09-10).

- **Spike B insertion matrix** — terminal output of `swift run SpikeBInsert`
  across several apps, showing the `ax / paste / type` columns with
  `LANDED` / `NOT FOUND`. The Terminal.app row (ax "ok" but NOT FOUND) is the
  interesting one — the silent false-success.
- **Spike A focus test** — terminal showing `PASS — frontmost app and focused
  element both unchanged` for Notes, and the Slack `PARTIAL` line next to it.
- **Secure-input detection** — the `SECURE INPUT IS ACTIVE — insertion cannot
  work here.` line from the password-field run.
- **The matrix table in `spikes/README.md`** — the filled-in 9-row app × strategy
  table, as rendered markdown or a screenshot. Good as the anchor image.
- Optional: the grey-rectangle walking-skeleton panel over a Notes window, to
  show how deliberately ugly Phase 2 is.
