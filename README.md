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

Trusted publishing must already be configured for `publish.yml`. To release a new version:

```sh
bun pm version patch # or: minor / major
git push origin main --follow-tags
gh release create "$(git describe --tags --exact-match)" --generate-notes
```

Publishing the GitHub release runs the checks and publishes the matching package version to npm using OIDC. No long-lived `NPM_TOKEN` is required.

## License

MIT. The review rubric is adapted from OpenAI Codex under Apache-2.0; see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
