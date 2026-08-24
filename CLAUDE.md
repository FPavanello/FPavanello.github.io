# CLAUDE.md

Project guidance for Claude Code working on this repository.

## Strict rules (non-negotiable)

1. **Never work outside `C:\Users\Standard\Documents\Github\FPavanello.github.io`.**
   Do not read, create, modify, or delete files anywhere else on the machine
   (other repos, home directory, system folders). Temporary scratch files are
   the only exception and must go to the session scratchpad directory, never
   into another project folder.

2. **Never work outside the `claude-branch` branch.**
   Do not check out, commit to, rebase, merge into, or push `master` (or any
   other branch). Verify with `git branch --show-current` before any write.
   If the branch is not `claude-branch`, stop and ask.

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

Built on **academicpages**, a fork of the Minimal Mistakes Jekyll theme. The
repo was forked from the template and then filled in with Filippo's content,
so many template leftovers remain (demo pages in `_pages/`, sample images in
`images/`, orphaned entries in `_publications/`).

## Layout of the content

Content Filippo actually maintains:

| Path | Purpose |
|---|---|
| `_pages/about.md` | Homepage — bio, upcoming talks, news |
| `_pages/publications.md` | Peer-reviewed papers, policy work, book chapters |
| `_pages/wp.md` | Working papers + work in progress |
| `_pages/cv.md` | Short CV (full PDF in `files/CV.pdf`) |
| `_pages/teaching.md` | Teaching + thesis supervisions |
| `_pages/seminars.md` | Presentations by year |
| `_data/navigation.yml` | Top navigation bar |
| `_config.yml` | Site + author metadata, social links |
| `files/` | PDFs (papers, slides, CV) |
| `images/` | Profile photo and figures |

Template leftovers that are **not** linked from the nav and can be ignored or
removed: `_pages/markdown.md`, `_pages/terms.md`, `_pages/archive-layout-with-content.md`,
`_pages/non-menu-page.md`, `_pages/portfolio.html`, `_pages/talkmap.html`,
`_pages/teaching.html`, and the sample images in `images/`.

## Build notes

- **Ruby, Bundler, Jekyll, and Node are not installed on this machine.** The
  site cannot be built or served locally. Do not suggest `bundle exec jekyll
  serve` as a way to preview.
- To show Filippo how a change will look, build a self-contained static HTML
  prototype in the scratchpad and publish it as an Artifact.
- GitHub Pages builds from `master` in safe mode, so only the plugins in the
  `whitelist:` block of `_config.yml` are available. Do not add plugins that
  GitHub Pages does not support.

## Conventions

- Filippo's name is bolded in author lists: `**Pavanello, F.**`.
- Abstracts are collapsed behind `<details><summary>Abstract</summary>`.
- Paper links follow the pattern `[ [Draft](...) &#124; [Working Paper](...) ]`.
- Internal file links are absolute: `https://fpavanello.github.io/files/....pdf`.
