# QBE mirror

A mirror of [QBE](https://c9x.me/compile/), the compiler backend, from its upstream repository `git://c9x.me/qbe.git`. The [Cesium devkits](https://github.com/cesiumlang/devkits) build QBE from here, so that a devkit build does not depend on one server.

## Branches and tags

- `master` and the tags (`v1.0` and later) are upstream's, unchanged. They only grow: a commit or tag, once mirrored, is never rewritten, moved or deleted.
- `main`, the default branch, is the mirror's own: this readme and the sync workflow. Upstream's history never reaches it.
- Upstream's other branches (`dev`, `loopopt`) are work in progress there and are not mirrored.

## Sync

The **Sync** workflow (`.github/workflows/sync.yml`) runs nightly and by hand (`gh workflow run sync.yml -R cesiumlang/qbe`). It fetches upstream's `master` and tags, trying `git://c9x.me/qbe.git` and then `https://c9x.me/git/qbe.git`, and pushes what is new. It fails when upstream cannot be reached, or when upstream rewrote `master` or moved a tag; rulesets refuse force pushes to `main` and `master` and changes to tags in any case.

GitHub disables scheduled workflows in a public repository after 60 days without activity. When upstream is quiet that long, enable it again: `gh workflow enable sync.yml -R cesiumlang/qbe`.

## Issues and changes

Report problems with QBE itself upstream, as its [home page](https://c9x.me/compile/) says. Issues with the mirror itself go to [cesiumlang/devkits](https://github.com/cesiumlang/devkits/issues).

## License

QBE is MIT licensed; see `LICENSE` on `master`. The mirror's own files on `main` are MIT as well.
