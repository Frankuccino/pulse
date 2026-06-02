# Pulse

A minimalist ledger for maintaining consistent daily engineering activity. This repository serves as the "heartbeat" of my development workflow, ensuring a continuous record of progress and maintaining my contribution momentum.

## How it works
`pulse` tracks my daily technical output. By appending journal entries and back-dating commits, it ensures that even on high-intensity research days where I might not push code to a main project, the "pulse" of my development remains visible and consistent.

## Bulk Backfilling
If you need to sync historical dates to maintain your contribution graph, use this loop:

```zsh
dates=(
  "2026-04-08" "2026-04-12" "2026-04-15" "2026-04-16" "2026-04-18"
  "2026-04-19" "2026-04-20" "2026-04-21" "2026-04-24" "2026-04-26"
  "2026-04-27" "2026-04-29" "2026-04-30" "2026-05-03" "2026-05-09"
)

for d in "${dates[@]}"; do
  echo "Journal entry for $d" >> history.md
  git add history.md
  GIT_AUTHOR_DATE="$d 12:00:00" \
  GIT_COMMITTER_DATE="$d 12:00:00" \
  git commit -m "docs: add journal entry for $d"
  echo "Committed for $d"
done
```
