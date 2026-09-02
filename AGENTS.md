# PickArena

CLI benchmark runner for AI coding models on Dart and Flutter task corpora, plus a static SvelteKit leaderboard. Dart package in `app/`, site in `web/`, task bundles in `tasks/flutter/`.

```
cd app && dart pub get && dart analyze && dart test
bun install && bun run web:check && bun run web:smoke
bun run check     # dart analyze + dart test + web check
```

Things you can't guess:

- The CLI needs only Dart and system SQLite, but a full `dart test` compiles the Flutter task fixtures. Install Flutter and run `bash scripts/warm-flutter-task-pub-cache.sh` first. CI runs Dart tests with `--concurrency=1`.
- Provider API keys come from `DART_ARENA_API_KEY_<PROVIDER_ID>` or a provider's `apiKeyEnv`, otherwise from `~/.dart_arena/settings.json`. A key found in the environment is stripped from that file on write.
- Official runs need Bubblewrap and refuse a dirty worktree, because admission provenance records git state. `scripts/regenerate-admissions.sh` regenerates QA reports. The task-QA CLI exits 0 even when a task is rejected, so read `rejectedTaskCount` from its JSON.
- `.factory/` is gitignored run output, never canonical plans. Plans and specs live in `docs/plans/` and `docs/specs/`; move finished ones into `old/` instead of deleting them.
- Re-hash leaderboard fixtures with `bun run leaderboard:fixtures:hash` after editing them.
