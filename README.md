# snparcher.github.io

Builds and deploys the snpArcher documentation site to GitHub Pages at
<https://snparcher.github.io>.

**The docs are authored elsewhere.** All content and site configuration live in
[`harvardinformatics/snparcher`](https://github.com/harvardinformatics/snparcher)
under `website/` (markdown in `website/docs/`, theme/nav in
`website/zensical.toml`). Edit the docs there — in the same PR as the code
change they document.

This repo only runs `.github/workflows/deploy.yml`, which:

1. Checks out `harvardinformatics/snparcher`,
2. Builds the [Zensical](https://zensical.org) site from `website/`, and
3. Publishes it to GitHub Pages.

## When it rebuilds

- **On docs changes** — snpArcher's `notify-docs.yml` workflow sends a
  `repository_dispatch` (`docs-updated`) here whenever `website/**` changes on
  its `main` branch (site updates in ~2 minutes).
- **Nightly** — a scheduled run acts as a self-healing fallback.
- **Manually** — via the "Run workflow" button on the *Build & deploy docs*
  workflow.

The dispatch relies on the `DOCS_DEPLOY_TOKEN` secret stored in the snpArcher
repo (a token with write access to this repo).
