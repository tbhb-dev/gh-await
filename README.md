# The gh-await project

A Go project with two command-line binaries, `gh-await` and `gh-awaiter`, built on the shared [devtools](https://github.com/tbhb-dev/devtools) toolchain.

## Development

[mise](https://mise.jdx.dev) pins the toolchain and runs the tasks. Run `mise run bootstrap` once, then `mise run check` before pushing. [AGENTS.md](AGENTS.md) is the contributor guide.

The binaries in `cmd/gh-await/` and `cmd/gh-awaiter/` each expose a `version` command. Shared metadata comes from `internal/buildmeta/`. To build both binaries in `bin/`, use `mise run build`, then run `bin/gh-await version` or `bin/gh-awaiter version`. For a source run with the same metadata flags, use `mise run run gh-await version`. A plain `go run ./cmd/gh-await version` uses the runtime build-info fallback for the version and leaves the commit and date empty.

Go checks run through `mise run lint-go-all`, with a separate formatting check at `mise run lint-go-fmt`. Coverage thresholds apply through `mise run cover-go`. To check for data races, use `mise run test-go-race`. Refresh dependencies with `mise run vendor`, then check for dependency drift with `mise run vendor-check`. The drift gate also detects files outside the index. Go tool directives pin analysis tools, whose sources join app dependencies in `vendor/`.

## License

Apache-2.0. See [LICENSE](LICENSE).
