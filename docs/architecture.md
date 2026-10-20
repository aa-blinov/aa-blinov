# Architecture

How aa-blinov is put together.

The repository is a page and the scaffold the house standard puts around a
page. There is one file a visitor reads, `README.md`, and the rest of the
tree exists so that a pull request can be checked before the page changes.
The code lives in the other repositories of the same account.

## The shape

Nothing is compiled and nothing is installed. The unit of work is a Markdown
file, and the unit of release is a commit on `master` that GitHub renders
without a build step.

| Path | What it is responsible for |
| --- | --- |
| `README.md` | The profile page. The only file a visitor sees, and the only one that changes when the owner's work changes. |
| `PRODUCT.md` | What the page is for, and what it must not turn into. |
| `AGENTS.md` | The re-entry surface: the commands, the layout and the traps of this repository. |
| `DESIGN.md` | The visual record, and the statement that the page owns no style of its own. |
| `docs/README.md` | The index of this folder. |
| `docs/architecture.md` | This document. |
| `docs/screenshots/README.md` | Why the repository carries no images. |
| `.github/workflows/house-style.yml` | The standard, enforced on every pull request. It calls the checker in `aa-blinov/golden-repo` at a pinned tag. |
| `.github/workflows/ci.yml` | The scaffold CI. It has no command to run, because there is nothing to run. |
| `.github/ISSUE_TEMPLATE/` | The forms GitHub shows when somebody opens an issue on the repository. |
| `LICENSE` | MIT, the terms the page and the documents ship under. |
| `src/`, `tests/`, `scripts/` | Empty placeholders. The standard's tree asks for the directories, and a repository with no code leaves them empty rather than filling them. |

## The data flow

Reading:

```
visitor -> github profile -> README.md -> rendered markdown -> one screen
```

Publishing:

```
pull request -> house-style.yml -> housecheck.py --strict -> master -> the public page
```

The page has no runtime, no request handler and no state. The only input is
the Markdown, and the only output is what GitHub's renderer makes of it.
The check between the two is the house-style workflow, which reads the
repository as it is on the pull request and fails the build on a broken
link, an emoji, a missing section or a document that is still a template.

## Decisions worth knowing about

### The repository name is the feature

GitHub renders the `README.md` of a repository whose name matches the owner
on that owner's profile page. That is the whole mechanism, and it is why
`aa-blinov/aa-blinov` cannot be renamed to `profile` without taking the
page off the profile. The name is part of the product.

The cost of that choice is that the repository cannot be a normal project.
There is no code, no build and no dependency, and anything that needs them
belongs in a different repository of the same account.

### The page is plain Markdown, and stays that way

GitHub's profile renderer drops most HTML and all scripts, so a layout that
depends on them works in a local checkout and nowhere else. The page uses
headings, lists, badges, a blockquote, a code fence and a rule, and
nothing else. The cost is that the page cannot be laid out precisely, which
is the point: it is read once, quickly, on whatever device the reader has.

### The standard is pinned by tag, and never vendored

`house-style.yml` calls `aa-blinov/golden-repo/.github/actions/house-style`
at tag `v1.0.3`, and `dependabot.yml` is told to leave that reference
alone. The checker therefore lives in one place and every adopting
repository runs the same code, and a change to the standard arrives as a
pull request rather than as a copy.

The cost is that the check cannot be run from a checkout of this repository
alone. It needs the standard's repository next to it, which is what
`AGENTS.md` shows.

### The workflows listen for `main`, and the branch is `master`

Both workflows declare `push: branches: [main]`, and this repository's
default branch is `master`. A push straight to `master` starts neither of
them, so the check runs on pull requests only. The standard's own HS100
rule is meant to catch this and does not, because its pattern never
captures the branch list.

The page is therefore only ever published through a pull request, which is
the safe order anyway. Nothing in the repository depends on the direct
push.

### The scaffold directories stay empty

`src/`, `tests/` and `scripts/` exist because the standard's tree names
them, and each holds a `.gitkeep`. A repository with no code that invents
code to fill them would be claiming work that does not exist.

## Boundaries

- **`README.md` may not carry anything but the page.** No build output, no
  vendored assets, no generated index. The file is edited by hand, and the
  pull request shows the whole change.
- **The page may not link outside the repository except to the owner's own
  pages.** A link to a file that is not in the tree does not resolve for a
  reader who cloned the repository.
- **The standard's documents may not be edited to pass the check.** The
  checker reads the repository as it is, and a rule that cannot be checked
  is a preference that goes in `AGENTS.md`.
- **`src/`, `tests/` and `scripts/` take no code.** The page has no
  runtime, so anything placed in them would have to be run by a person.
