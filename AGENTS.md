# AGENTS.md — agent context for `aa-blinov`

The GitHub profile repository of Alexander Blinov. One file, `README.md`, which GitHub renders on the profile page at <https://github.com/aa-blinov>. There is no code, no build and no dependency here; the code lives in the other repositories of the same account.

This file is what you need to work on the profile without reading the rest of the repository.

## Run / build / test

```bash
git clone https://github.com/aa-blinov/aa-blinov.git          # the profile page
git clone https://github.com/aa-blinov/golden-repo.git         # the standard, and the checker
python3 golden-repo/scripts/housecheck.py --strict /path/to/aa-blinov
```

There is nothing to install, no test suite and nothing to build. The house check is the only gate, and CI runs it on every pull request.

## Where things live

| Path | What it holds |
| --- | --- |
| `README.md` | The profile page. GitHub renders it at <https://github.com/aa-blinov>. |
| `AGENTS.md` | This file. |
| `PRODUCT.md` | What the page is for, and what it must not turn into. |
| `LICENSE` | MIT, the terms the page and the documents ship under. |
| `.github/workflows/house-style.yml` | The standard, enforced. It pins `aa-blinov/golden-repo` at v1.0.3. |
| `.github/workflows/ci.yml` | The scaffold CI. It has no command to run, because there is nothing to run. |
| `docs/` | The index of the documents, and the architecture note. |

The rest of the standard's tree is still a scaffold: `CHANGELOG.md`, `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md`, `DESIGN.md`, `docs/README.md` and `docs/architecture.md` carry the template marker and have not been written. Each one is a separate change, and each one needs somebody who knows the subject to answer its questions.

## Traps

- **The README is the profile page.** GitHub renders the `README.md` of a repository named after its owner on that owner's profile. Every word is public the moment it is pushed, and there is no preview to check it in first.
- **The repository name carries the page.** `aa-blinov/aa-blinov` is the name GitHub looks for. Renaming the repository takes the page off the profile.
- **The default branch is `master`, and the workflows listen for `main`.** Both `ci.yml` and `house-style.yml` declare `push: branches: [main]`, so a push to `master` starts neither of them. They run on pull requests only, and the checker's own HS100 rule reports the mismatch.
- **The standard is pinned, not vendored.** `house-style.yml` calls `aa-blinov/golden-repo/.github/actions/house-style@v1.0.3`, and `dependabot.yml` is told to leave that reference alone. A change to the standard arrives here as a pull request from `golden-repo`, and nothing in this repository has to be updated for it.
- **The old page carried an emoji, and the checker bans them.** The first commit was GitHub's own profile template, emoji included, and the basketball in the Interests line came from there. HS040 fails the build on any emoji in any file, so the page and the check disagreed until the text was rewritten.
- **The old page spelled "Containerization" with a Cyrillic Es (U+0421) in place of the Latin C.** The checker passes it, and a search for "Containerization" does not find the line. Copying the word out of the old README copies the homoglyph with it.
- **The job titles are the owner's statement.** Nothing in this repository verifies "Tech Lead" or the employers. The last edit was made by hand on 2026-03-13, in commit `e999314`, which changed the title from CTO and added the missing final newline at the end of the file.
- **The page is one screen.** It is read in a browser, often on a phone, by a reader who came from a link and has to decide in a few seconds whether to go further.

## Style / safety rails

- **No emoji, in any file.** The checker enforces it (HS040).
- **Facts over adjectives.** A claim names the role, the tool or the number.
- **Do not rewrite what the page says about the owner's work.** The roles, the employers and the areas of expertise are the owner's own statements, and they change when the owner changes them.
- **Do not invent history.** No download counts, no testimonials, no usage numbers: the repository holds one file, and there is nothing to count.
- **Keep the page short.** One screen of summary, then the links.
- **Comments explain why, never what.**
