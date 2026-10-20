# Screenshots

This repository carries no images.

The product is one Markdown file rendered by GitHub on a profile page, and
there is no interface of its own to photograph. A screenshot of the profile
would be a picture of GitHub's renderer, and it would go stale the moment
GitHub changed a colour.

The repository therefore has an empty `docs/screenshots/` directory and no
image references anywhere in it. The house-style checker verifies that
every image reference resolves to a file that exists, and with no
references there is nothing that can break.

If a future version of the page grows a diagram or a screenshot of
something the owner made, the file goes here and the reference goes into
`README.md` by relative path, so it resolves on GitHub and in a local
checkout alike.
