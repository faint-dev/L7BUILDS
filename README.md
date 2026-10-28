# L7BUILDS

macOS builds of [L7CODE](https://l7code.vercel.app), produced on GitHub's public-repo runners so the private source repo does not spend Actions minutes.

`Build macOS` (`.github/workflows/build-macos.yml`) is `workflow_dispatch` only. It:

1. checks out `lawrence-millard/l7code` at the ref you pass, using a read-only deploy key;
2. installs the workspace with Vite+;
3. runs `vp run dist:desktop:artifact --platform mac --target dmg --arch arm64`;
4. publishes `release/L7CODE-<version>-arm64.dmg` and `.zip` to a `v<version>` release here.

Required secret: `SOURCE_DEPLOY_KEY`, the private half of a read-only deploy key on `lawrence-millard/l7code`.

The builds are ad-hoc signed, not notarized.
