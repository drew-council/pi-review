# @bizmyth/pi-review

A read-only branch review command for the [Pi coding agent](https://github.com/earendil-works/pi-mono).

`/review` asks the active model to inspect the current branch against a base branch and return prioritized, actionable findings without modifying the working tree.

## Install

```sh
pi install npm:@bizmyth/pi-review
```

Restart Pi after installation, then run:

```text
/review              # compare against main
/review develop      # compare against another base branch
```

The command requires a Git working tree, a checked-out branch, and a locally resolvable base branch. Pi extensions run with your full user permissions; review their source before installation.

## Development

```sh
bun install
bun run check
```

`bun run check` runs Biome formatting and lint checks, TypeScript 7 (`tsgo`) type checking, and Bun tests.

## Releasing

1. Update `version` in `package.json` and commit the lockfile.
2. For the initial release, run `npm publish` locally.
3. In the npm package settings, configure GitHub Actions trusted publishing for `.github/workflows/publish.yml`.
4. For later releases, create a GitHub release whose tag exactly matches `v<package.json version>`.

The publish workflow uses npm trusted publishing (OIDC), so it does not require a long-lived `NPM_TOKEN`.

## License

MIT. The review rubric is adapted from OpenAI Codex under Apache-2.0; see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
