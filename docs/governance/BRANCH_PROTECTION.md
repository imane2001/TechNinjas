# Branch Protection Rules – TechNinjas

This document describes the branch protection settings applied to the `main` branch.

---

## 🔒 Protection Settings

- **Require pull request reviews before merging**
  - At least 1 approval required
  - Stale approvals dismissed when new commits are pushed

- **Require status checks to pass before merging**
  - CI workflow (`ci.yml`) must be green
  - Lint and test jobs enforced

- **Require branches to be up to date before merging**
  - PRs must be rebased or merged with latest `main`

- **Restrict who can push to `main`**
  - Direct pushes disabled
  - Only squash merges via PR allowed

---

## 📸 Evidence

Include a screenshot of the GitHub branch protection settings page here for audit purposes.

---

## 📝 Notes

- These rules ensure clean history, enforce CI, and guarantee peer review.
- Settings are reviewed periodically and updated as team size or workflow evolves.