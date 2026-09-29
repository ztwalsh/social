# Ground-truth code reviewer (2026-09-29)

- The reviewer's FAIL on the planted sloppy diff (5 violations, each citing a DESIGN.md section)
- The FAIL on my own real commit: "DESIGN.md claims 20px phone gutter site-wide; inner pages use 40px"
- The PASS on the fix
- Optional: the 11-rule repo checklist, to show rules come from the doc, not generic advice
- Lint ticket: round 1 FAIL (formatter would rewrite tokens.css), round 2 FAIL (would delete frontmatter comments in 10 files), round 3 PASS
- Terminal: 12 pixel-diff comparisons all "diffpx=0" after the format pass
