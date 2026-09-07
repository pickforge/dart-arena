The CLI needs Dart and system SQLite, but the full Dart suite compiles Flutter task fixtures. Warm their dependencies with `bash scripts/warm-flutter-task-pub-cache.sh` first; CI uses `--concurrency=1`.

Provider keys come from `DART_ARENA_API_KEY_<PROVIDER_ID>` or `apiKeyEnv`, then `~/.dart_arena/settings.json`. A key supplied through the environment must be removed from that file on write.

Official runs require Bubblewrap and a clean worktree for admission provenance. `scripts/regenerate-admissions.sh` regenerates QA reports. Task-QA can exit 0 on rejection, so inspect `rejectedTaskCount` in its JSON.

`.factory/` is ignored run output, not canonical plans. Keep plans in `docs/plans/` and specs in `docs/specs/`; archive finished documents in their respective `old/` subdirectories rather than deleting them. Re-hash changed leaderboard fixtures with `bun run leaderboard:fixtures:hash`.
