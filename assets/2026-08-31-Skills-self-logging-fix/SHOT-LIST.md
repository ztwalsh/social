# Shot list — social-log fixes its own blind spot

- BUILD-LOG.md open to the 2026-08-31 · Skills · 48bccd6 entry (the one that
  describes this fix), so the log is visibly recording its own change.
- Terminal scrollback showing the `cd ~/sites/personal-projects/Skills && git
  commit …` one-liner that triggered it — the exact command shape that used to
  slip through.
- Optional: the hook's fallback-scan block in post-commit-capture.sh (the
  `for d in "$ROOT"/*/` loop) for a "here's the ~15 lines that fixed it" shot.
