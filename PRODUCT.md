# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

The product is a page. One Markdown file, rendered by GitHub on the owner's profile at <https://github.com/aa-blinov>, above the list of repositories the account publishes. There is no application, no server of its own, no build step and no dependency. The repository description on GitHub says it in one line: "Config files for my GitHub profile."

## Users

Two readers, in the order they arrive:

- **Someone deciding whether to talk to this person.** A recruiter, a colleague or a team lead with the profile link and a few seconds to spend on it. The page has to name the roles, the areas of work and the way to reach the owner.
- **Someone looking for the work.** A developer who arrived from a link inside a repository, or who found the account while looking for a name. For that reader the page is a directory, and the repositories under it are the content.

The owner states the second audience at the end of the page: open to collaboration on AI projects, research and technical consulting.

## Product Purpose

The repository exists to make one sentence true for a visitor: this is who Alexander Blinov is, what the owner builds, and how to reach the owner.

Everything in the file serves that sentence. The roles come first because they answer who, the areas of work answer what, and the links at the end answer how.

Success for the visitor: after one screen the roles, the areas and the way to write are known. Success for the owner: the page says the same thing on every visit, and nobody has to edit it for that to be true.

## Positioning

The GitHub-native profile. The alternatives are a personal site or a CV: both are documents about the person, kept away from the code, and both go out of date as soon as the work changes. Here the page and the repositories sit under one account, and the profile is the directory for them.

The judgement behind the wording: a repository named after its owner is a page first and a repository second. The file that matters is `README.md`, and it is written for a browser rather than for a terminal.

## Operating Context

The page is read in a browser, often on a phone, by a reader who arrived from a link. It is read once and quickly, and the reader either has a next step or they do not.

The repository itself changes rarely: three commits on `master`, the last of them on 2026-03-13. The house standard's workflow checks every pull request against the checker in `aa-blinov/golden-repo`, so the page is edited in a pull request and read before it is public.

## Capabilities and Constraints

Confirmed by the repository:

- The profile is one file. On `master` it is the only file in the repository.
- It names two roles and links their employers: Tech Lead at EORA, Senior Back-end Developer at Novosibirsk State Technical University.
- It names four areas of expertise and one contact route, LinkedIn.
- GitHub renders it as the profile page, because the repository is named after its owner.
- The standard's tree adds the rest: an MIT licence, the house-style workflow, the CI scaffold, the document index and the community files.

Constraints a change has to respect:

- No build step, no dependency and no test suite. Work that needs them belongs in another repository.
- The checker bans emoji in every file, including this page.
- The page is written in English, for a reader outside the field.
- The default branch is `master` while the workflows in the standard's tree listen for `main`, so a push to `master` starts neither of them.

Deliberately not true, and worth knowing before a change:

- The page makes claims about a person that the repository cannot verify. The roles, the employers and the areas of expertise are the owner's statements.
- There are no usage numbers, and nowhere to put them: the repository holds one file.
- The page carries no CV, no photograph, no list of talks and no list of publications.

## Brand Commitments

**Name:** Alexander Blinov. **Voice:** plain, technical, first person. The page names the tools and the roles instead of describing them in adjectives.

The promise the page keeps: a visitor knows what the owner builds and how to reach the owner after one screen. The LinkedIn link is part of that promise, and it is the only contact route on the page.

## Evidence on Hand

- `README.md` on `master`: the roles, the areas of expertise, the LinkedIn link and the interests.
- The repository description on GitHub: "Config files for my GitHub profile."
- Three commits on `master`, the last of them on 2026-03-13, which changed the job title and added the missing final newline.
- The branch `standard/adopt-the-house-standard-aa-blinov`: the house file set, with the document templates still unwritten.

Absent, and not to be invented: no usage numbers, no testimonials, no awards, no comparison with other engineers, and no claim that the technologies in the expertise list are the ones in use at a given employer.

## Product Principles

1. **One screen, then the links.** The page names the roles, the areas and the way to reach, and stops there. The rest lives in a repository.
2. **Name the tool, not the adjective.** "Distributed systems design" is a fact. "Cutting-edge solutions" is not, and the house style bans the second kind.
3. **The words belong to the owner.** Nothing about the roles, the employers or the expertise is written on the owner's behalf by somebody else.
4. **English on the page.** The reader is whoever found the link.
5. **No emoji.** The checker fails the build on them, and the first version of this page carried one from GitHub's own template.

## Accessibility & Inclusion

- **The page is plain Markdown.** GitHub renders the headings, the lists and the links, and there is no custom layout that can break.
- **The language is English, and the original is not translated.** The areas of expertise and the roles are named in the language the tools use.
- **A standard for the page itself has not been set.** The contrast and the semantics are GitHub's, and the owner has recorded no requirement of their own.
- **The audience is wider than the field.** The page names the technologies instead of assuming them, and the two employers are spelled out rather than left to a logo.
