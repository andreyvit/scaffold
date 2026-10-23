# Bubblehouse evidence

Backend: `/Users/andreyvit/Developer/prairie/backend`, snapshot `aaa53bdc6fbda464d7d563d696ebca76719469ed` (2025-05-31). All refs counted: 4,395 Andrey non-merge commits / 6,469 before cutoff. Counts describe coverage candidates, not proof of every line.

`git blame --line-porcelain` verified authors. `-w -M -C` used when moves hid original authorship. References below are historical `revision:path`, not current line claims.

| ID | Evidence | Attribution / scope |
|---|---|---|
| B1 | `_readme/code.md:5–27` | All Andrey; stable wire names, enum exceptions, codegen cost. |
| B2 | `_readme/integrations.md:6–20` | All Andrey; purpose and cost of integration boundary. |
| B3 | `_readme/bolt.md:8–34` | All Andrey; scaling limits and measured tradeoffs; concerns, not guarantees. |
| B4 | `_readme/backups.md:4–46` | All Andrey; transport choice and local restore workflow. |
| B5 | `_readme/web.md:24–32`, `_readme/js.md:4–14` | All Andrey; host auth, Turbo, Stimulus, runtime bundles. |
| B6 | `README.md:262–280` | Authorship checked; preserve known gaps and proposed work as such. |
| B7 | `fire/firemetrics/firemetrics.go:9–25` | All Andrey; request/job/business counters. Legacy `da984fb8` adds context-based logging; `19fa6ff2` logs slow unnamed DB calls. |
| B8 | `fireback/jobs.go:47–85,175–270` | All Andrey; crashed-job recovery, counters, persisted retries/failure. |
| B9 | `fdb/load.go:51–56,58–64`; `fireback/errors.go:41–69` | Customer body traces to Andrey `d221b435d6`; product loader is Andrey `97cc2c4281`; public-error path all Andrey. Do not attribute other loaders. |
| B10 | `fire/firetesting/testapp.go:67–86,126–210` | Andrey except one later Stanislav line; real app, test DB, fake clock, HTTP replay. |
| B11 | legacy `6a961d759127aba3c07fea9b89bbb8937c5a0ac6`, `core/nfts.go`, `r_nfts_test.go` | Andrey; receipt outcomes and orphaned-purchase scenario. |
| B12 | legacy `9da0cdc27dbc6e455b97dfe73c709194d9702fdf` | Andrey; PostgreSQL skeleton and explicit routes. |
| B13 | legacy `be478b50f6f194b762ad09544c1e6c7594c3384d` | Andrey; cohort-style retention query. Evidence of measuring retention, not proof of a product-metrics philosophy. |

Legacy repo: `/Users/andreyvit/Developer/prairie/legacy`. 2,131 / 3,725 eligible non-merge commits by Andrey. Examined selected 2019–2021 changes, not all commits.

## Mobile sources

Archive: `/Users/andreyvit/Developer/prairie/Bubblehouse_2022_ios.zip`. Contains `.git`; read-only extraction in `/tmp/scaffold-bubblehouse-ios`. HEAD `9b9a083d838aabce935f2447fcb201ce2a8c9729` (2023-03-30). 156 Andrey commits in all-ref shortlog including merges. Original archive retained.

| ID | Andrey commit | Evidence |
|---|---|---|
| M1 | `541907bf5c304f90465e429cfbf4bd4b8232ab21` | Commit rationale + `Blurr/View/AddModule/PickAssets/PickAssetsGridView.swift` diff. |
| M2 | `11698b1f5e1007c69b15ffb52ce6bae6aacae172`; `08e26fd2146b212be5ca128bd121da84a22f2c06` | Follow/unfollow local update and later count correction. |
| M3 | `44a0a9860139e8bfb184667af8f139dd823bb525:Blurr/Services/VotingService.swift:10–37` | Authored comment edit; rationale for bounded queue and deferred complexity. Remaining source inspected for context. |
| M4 | `a43fcf4cbad51d64bdd4a402b85f22ffb31e77a3`; `d109b152572e30f750df09fc05dc230647666195` | Batch interactive votes; view-duration metrics. |
| M5 | `129f918e5232e499753b95454ea68d0db87da45e` | Auth-token ownership correction; commit message and diff. |

## Excluded / caveats
- `_readme/infra.md`: 114/163 lines Stanislav; only 49 Andrey. No blanket infrastructure-policy inference.
- `fireback/health.go` mmap-gap checks: Stanislav. Andrey wrote original token-gated disk-space check (`7f2c770ca6`).
- iOS `62bd2208` style guide explicitly describes Filip’s conventions despite Andrey’s Git author.
- Android `/Users/andreyvit/Developer/prairie/android`: no Andrey match in pre-cutoff author census. No attribution.
- Historical production details are not current operating guidance; no production access or changes made.
