# Live validation: target 67bda9a8 (base 9224c902), OpenCode 2.2.4, macOS arm64, host load about 23-33

| Case | Driver | Result |
|---|---|---|
| Two locations on one OpenCode server: A gets neither B's turn-end warning nor its startup nudge, and B's busy record is untouched; B's own session drives all three | tests/fm-opencode-primary-live-e2e.test.sh (real opencode 2.2.4 server, private HOME/XDG/db) | PASS (opencode-live-e2e-rerun.log, exit 0) |
| Marked secondmate home: two notified, handled, acknowledged cycles with a live identity-matched successor | same live e2e | PASS |
| Primary under a foreign lock owner is refused arming and warned, then arms once it owns the lock | same live e2e | PASS |
| Watcher/plugin fixture migration (fm-primary-scope-lib, session.get mocks, removed global arm) | tests/fm-pi-watch-extension.test.sh | PASS 69/69 |
| Turn-end guard scope, including secondmate and cross-location | tests/fm-turnend-guard.test.sh | PASS 95/95 |
| SessionStart nudge scoped to its own location | tests/fm-sessionstart-nudge.test.sh | PASS 26/0, exit 0 (sessionstart-nudge.log) |
| Busy-state plugin ignores other locations' and unplaced sessions on a shared server | tests/fm-busy-adapter-wiring.test.sh | PASS: 17 ok / 0 not ok, including the new OpenCode 2 cases, before the 900 s cap (exit 124 at load about 30; busy-adapter-wiring.log) |
| Claude secondmate stall-gate "frozen queue" cases (not OpenCode) | fm-busy-adapter-wiring | Flaky under load. Base 9224c902 fails the same group ("stall gate never observed the frozen queue"), so this predates the change (busy-adapter-wiring-BASE-9224c902.log) |
| fm-watch-arm identical re-append byte-identity | tests/fm-watch-arm.test.sh | Known baseline failure that reproduces on base (fm-watch-arm-base.log) |
