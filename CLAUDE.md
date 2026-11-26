# CLAUDE.md

Project guidance for Claude Code working on this repository.

## Strict rules (non-negotiable)

1. **Never work outside `C:\Users\Standard\Documents\Github\FPavanello.github.io`.**
   Do not read, create, modify, or delete files anywhere else on the machine
   (other repos, home directory, system folders). Temporary scratch files are
   the only exception and must go to the session scratchpad directory, never
   into another project folder.

2. **Work on `master`, and only `master`.**
   The redesign branch `claude-branch` was merged in August 2026 and Filippo
   now edits `master` directly, so that is where changes go. Do not create,
   check out, rebase or merge other branches without being asked. Verify with
   `git branch --show-current` before any write; if it is not `master`, stop
   and ask. `previous-version` holds the pre-redesign site and is never to be
   modified — it is the rollback.

3. **Never commit or push without explicit approval.**
   Show the diff and let Filippo review the rendered result first. `git add`,
   `git commit`, `git push`, and `gh pr create` all require him to say so in
   that session. Approval for one commit is not approval for the next.

4. **Never touch the upstream remotes.** `origin` and `upstream` are read-only
   here. No force pushes, no branch deletions, no tag operations.

## What this site is

Academic personal website for Filippo Pavanello (applied environmental
economist, ifo Institute / LMU Munich), published at
https://fpavanello.github.io via GitHub Pages.

Built on **academicpages**, a fork of the Minimal Mistakes Jekyll theme,
redesigned in August 2026. The site layer lives in `_sass/_ledger.scss`,
`_includes/masthead.html`, `_includes/author-profile.html` and
`_includes/paper.html`; the rest is upstream theme.

The profile panel appears on the homepage only — every other page sets
`author_profile: false` and leaves that grid column empty, so content keeps
the same horizontal position throughout.

## Layout of the content

Content Filippo actually maintains:

| Path | Purpose |
|---|---|
| `_pages/about.md` | Homepage — bio, upcoming talks, news |
| `_pages/publications.md` | Peer-reviewed papers, policy work, book chapters |
| `_pages/wp.md` | Revisions & under review, working papers, work in progress |
| `_pages/cv.md` | Short CV (full PDF in `files/CV.pdf`) |
| `_pages/teaching.md` | Courses. Thesis supervision is commented out but kept |
| `_pages/seminars.md` | Presentations by year |
| `_data/navigation.yml` | Top navigation bar |
| `_config.yml` | Site + author metadata, social links |
| `files/` | PDFs (papers, slides, CV) |
| `images/` | Profile photo and figures |

The template's demo pages and sample images were deleted in the redesign.
`CLAUDE.md`, `README.md`, `CHANGELOG.md` and `images/papers/README.md` are in
`exclude:` — without that, `jekyll-optional-front-matter` and
`jekyll-readme-index` publish them as real pages.

## Build notes

- **Ruby, Bundler and Jekyll are not installed on this machine.** The site
  cannot be built or served locally. Do not suggest `bundle exec jekyll serve`
  as a way to preview unless Filippo installs Ruby first.
- **Node is available**, but only via the copy bundled with VS Code:
  ```
  ELECTRON_RUN_AS_NODE=1 "C:\Users\Standard\AppData\Local\Programs\Microsoft VS Code\Code.exe" script.js
  ```
  Useful for syntax-checking JavaScript. There is no `npm`, so packages
  cannot be installed.
- **Python 3.13 is installed** at `C:\Program Files\Python\Python313\python.exe`,
  with PyYAML. Call it by full path — the bare `python` on PATH resolves first
  to a Microsoft Store stub that only errors. Use it to validate `_data`
  before committing; it has caught every YAML break so far:
  ```
  "/c/Program Files/Python/Python313/python.exe" -c "import glob,yaml; [yaml.safe_load(open(f,encoding='utf-8')) for f in glob.glob('_data/**/*.yml',recursive=True)]"
  ```
- **Claude cannot `git push` from this environment.** The credential helper is
  Git Credential Manager, which needs a GUI prompt that never appears in a
  non-interactive shell, so the push hangs and then times out. Commit locally,
  then ask Filippo to push (he uses GitHub Desktop).
- Verification runs in CI: `.github/workflows/build.yml` parses every
  `_data/*.yml`, rejects non-ASCII in stylesheets, builds under `LANG=C`,
  checks each expected page exists and is non-empty, rejects unrendered
  Liquid, checks referenced figures exist, and rejects absolute production
  URLs and `//` comments in inline scripts. Check its result with:
  ```
  https://api.github.com/repos/FPavanello/FPavanello.github.io/actions/runs?branch=master
  ```
  Job logs need auth, so the failing *step* is visible via `.../runs/<id>/jobs`
  but its output is not — reproduce locally instead.
- **Inline `<script>` must not use `//` comments.** `_layouts/default.html`
  runs through `layout: compress`, which strips every newline, so a line
  comment swallows the rest of the script. Nothing throws; the code silently
  never runs. Use `/* */`. CI enforces this.
- To show Filippo how a change will look before it is pushed, build a
  self-contained static HTML prototype in the scratchpad and publish it as an
  Artifact.
- GitHub Pages builds from `master` in safe mode, so only the plugins in the
  `whitelist:` block of `_config.yml` are available. Do not add plugins that
  GitHub Pages does not support.
- **The theme fights back.** Upstream lays the page out with Susy floats, its
  nav is `display: table`/`table-cell` (plus "greedy nav" JavaScript that hides
  links it thinks overflow), and several colours are hardcoded white in
  `_reset.scss` and `_variables.scss`. `_sass/_ledger.scss` is imported last and
  overrides all of this. When adding overrides, check the theme's actual
  `display` value first rather than assuming flexbox.

## Content architecture

Papers and CV entries live in `_data/*.yml`, not in the page bodies:

| File | Feeds |
|---|---|
| `_data/publications.yml` | `/publications/` peer-reviewed list |
| `_data/working_papers.yml` | `/wp/` — `under_review:`, `working_papers:`, `progress:` |
| `_data/coauthors.yml` | co-author homepages, linked wherever a name appears |
| `_data/other_work.yml` | policy work and book chapters |
| `_data/cv.yml` | `/cv/` |
| `_data/teaching.yml` | `/teaching/` |
| `_data/talks.yml` | `/seminars/` and homepage upcoming talks |
| `_data/news.yml` | homepage news |

`_includes/paper.html` renders one paper entry, for both publications and
working papers (`kind="wp"` suppresses the venue line in favour of the status
pill).

**Figures are currently switched off** — `paper_figures: false` in
`_config.yml`. The images in `images/papers/` and the `figure:` fields in
`_data/publications.yml` are kept so the one setting turns them back on.
Working papers never show figures regardless.

## Conventions

These are applied by the templates, not typed into the data:

- Filippo's name is bolded automatically wherever it appears in an `authors:`
  string, via `author_key` in `_config.yml`. Write it plainly as
  `Pavanello, F.` — no markdown.
- Co-author names are linked from `_data/coauthors.yml`. A name must be keyed
  in every form it is written in: publications use `Surname, X.` and working
  papers `X. Surname`.
- Abstracts come from the `abstract:` field and are collapsed behind a
  disclosure by the template.
- Links come from a `links:` list of `{label, url}`, not hand-written markup.
- **Internal links are root-relative** — `/files/foo.pdf`, never
  `https://fpavanello.github.io/files/foo.pdf`. Absolute production URLs break
  preview deploys, which then load the live site's assets. CI rejects them.
- `_data` is indented with **spaces only**. A tab anywhere makes the file
  invalid YAML and the whole build fails.
- When moving an entry between `_data` files, re-check its indentation:
  entries nested under a key sit one level deeper than a top-level list, and
  a stray level silently folds following keys into the previous block scalar.
