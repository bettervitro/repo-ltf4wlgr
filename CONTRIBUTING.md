# Contributing to This Project

Thank you for considering contributing! Every kind of contribution helps:
code, documentation, bug reports, feature ideas, or design feedback.

Contributions from outside collaborators go through a **fork and Pull
Request** workflow — you work in your own copy of the repository and ask
us to merge your changes.

## Ways to Contribute

Not sure where to start? Look for issues labeled:

- [`good first issue`](../../issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22) — beginner-friendly tasks
- [`help wanted`](../../issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22) — where we'd love community help
- [`documentation`](../../issues?q=is%3Aissue+is%3Aopen+label%3Adocumentation) — docs improvements, no deep code knowledge needed

Typos, unclear docs, and missing examples count as real contributions — don't hold back.

## The Contribution Workflow

### 1. Fork the repository

Click the **Fork** button at the top of the repository page on GitHub.
This creates your own copy at `https://github.com/<your-username>/<repo-name>`.

### 2. Clone your fork (one-time setup)

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

Then connect your local copy to the original repo (called `upstream`) so
you can stay in sync:

```bash
git remote add upstream https://github.com/<org>/<repo-name>.git
git remote -v   # verify: origin = your fork, upstream = the original
```

### 3. Sync your local copy with the latest changes

Always start from an up-to-date `main`:

```bash
git checkout main
git pull upstream main
```

### 4. Create a branch for your change

Never commit directly to `main`:

```bash
git checkout -b fix/login-error
# naming: feat/<feature>, fix/<bug-or-issue-number>, docs/<topic>
```

### 5. Make your changes

Edit the files for your feature or fix. Before committing, review exactly
what you changed:

```bash
git status   # see which files changed
git diff     # review your edits line by line
```

If the project has checks (tests, linting, building), make sure they pass
before moving on — see the README for how to run them.

### 6. Stage your changes

Stage the specific files you want to include in the commit:

```bash
git add path/to/changed-file.ext
```

> ⚠️ Avoid `git add .` — it's easy to accidentally commit secrets,
> build artifacts, or unrelated debug changes.

### 7. Commit

Use a [Conventional Commit](https://www.conventionalcommits.org/) message:

```bash
git commit -m "fix(auth): show clear error message on failed login"
```

Format:

```
<type>(<optional scope>): <short imperative summary>

<optional body explaining *why*>

<optional footer: Fixes #42>
```

More examples:

```bash
git commit -m "feat(api): add pagination to /search endpoint"
git commit -m "fix(ui): prevent double-submit on login button

The button stayed clickable during the fetch, letting users
fire two identical requests. Disable it while loading.

Fixes #87"
```

| Prefix      | Use for                            |
|-------------|------------------------------------|
| `feat:`     | New feature                        |
| `fix:`      | Bug fix                            |
| `docs:`     | Documentation only                 |
| `refactor:` | Change that adds no feature or fix |
| `test:`     | Adding or correcting tests         |
| `chore:`    | Tooling, CI, housekeeping          |

Rules of thumb: summary under ~50 characters, imperative mood ("add", not
"added"), no trailing period. The body explains **why** — the diff shows
**what**. Reference the issue with `Fixes #<number>` if there is one.

### 8. Push to your fork

```bash
git push -u origin fix/login-error
```

Note: you push to `origin` (your fork), never to `upstream` (the original
repo — you don't have write access there).

### 9. Open the Pull Request

1. GitHub prints a link after pushing — click it, or go to **your fork's
   page** on GitHub and click **Compare & pull request**.
2. Make sure the direction is correct:
   - **base repository:** `<org>/<repo-name>`, base branch: `main`
   - **head repository:** `<your-username>/<repo-name>`, compare branch: yours
3. Describe in the PR:
   - **What** the change does and **why** (link the issue: `Fixes #42`)
   - **How you tested it**
   - Screenshots for UI changes
4. Submit.

**One PR = one thing.** A PR that fixes a bug, renames variables, and adds
a feature is three unreviewable changes stacked together — split it. Small,
focused PRs get reviewed in days; sprawling ones sit for weeks.

### 10. After submitting

- **CI runs automatically** (if configured) — if checks fail, fix locally
  and push again to the same branch; the PR updates itself. No new PR needed.
- **Address review comments** by pushing more commits to the same branch.
  Don't force-push — it erases the review history.
- **Mark conversations resolved** as you address each comment so reviewers
  can follow along.
- **Need more commits on the same PR?** Just keep working on the branch
  and push — every push updates the PR:
  ```bash
  git add <files>
  git commit -m "fix(auth): handle empty username case"
  git push
  ```

### 11. Once merged, clean up and resync

```bash
git checkout main
git pull upstream main     # brings the merged change into your local main
git push origin main       # update your fork's main too
git branch -d fix/login-error
git push origin --delete fix/login-error
```

## Keeping Your Fork Up to Date

Your fork drifts behind the original repo over time. Sync it regularly —
especially before starting new work:

```bash
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```

## Reporting Bugs

Open a [GitHub Issue](../../issues/new) on the **original repository** and include:

- What you did, what you expected, and what actually happened
- Steps to reproduce (minimal if possible)
- Your environment details (OS, versions, project version)
- Relevant logs or screenshots

Please search existing issues first — if one exists, add a 👍 and any extra
details there instead of opening a duplicate.

## Suggesting Features

Feature suggestions are welcome as issues. Please describe the **problem**
you're trying to solve, not just the solution you have in mind — this
helps us evaluate alternatives. For larger features, consider opening a
draft issue first to discuss the approach before investing time in
implementation.

## Pull Request Review Process

- Any automated checks must pass before maintainer review begins.
- At least one maintainer approval is required.
- Reviews aim to respond within **3 business days**; if nothing has
  happened, a friendly ping on the PR is welcome.
- Maintainers may ask for changes, or close PRs that are stale
  (30+ days inactive) or outside the project's scope.
- Merge strategy is squash-merge; commit history stays linear on `main`.

## Getting Help

- 💬 Ask in [Discussions](../../discussions) for design questions and ideas
- 🐛 Open an issue for bugs
- 📖 Read the [README](./README.md) for setup and architecture overview

## Security Vulnerabilities

**Do not open a public issue.** Contact the maintainers directly
(e.g. via the email listed in the README or repository settings) for
responsible disclosure.

## Code of Conduct

By participating in this project, you are expected to keep discussions
respectful and constructive. Report unacceptable behavior to the
maintainers.

## License

By contributing, you agree that your contributions will be licensed under
the project's license (see LICENSE).