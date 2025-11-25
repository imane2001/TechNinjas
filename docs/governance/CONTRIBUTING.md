# Contributing Guidelines – TechNinjas

Welcome to the TechNinjas repository! This guide outlines how we collaborate, contribute, and maintain quality across our codebase.

---

## 🔀 Branch Naming Convention

Use descriptive, lowercase names separated by slashes:

- `feature/<short-topic>` – new features
- `fix/<issue-id>` – bug fixes
- `docs/<topic>` – documentation updates
- `conflict/<brief-description>` – conflict resolution branches

---

## 🧾 Commit Style

Follow [Conventional Commits](https://www.conventionalcommits.org):

- `feat:` – new feature
- `fix:` – bug fix
- `docs:` – documentation only
- `chore:` – maintenance tasks
- `test:` – adding or updating tests
- `ci:` – CI/CD changes
- `refactor:` – code restructuring without behavior change

Example:  
`feat: add login form validation`

---

## 🔁 Workflow Model

We use **Mainline development** for simplicity and speed.

> Rationale: Our team is small, CI is fast, and we merge frequently. Mainline allows short-lived branches and squash merges into `main`, keeping history clean and velocity high.

---

## ⏱️ Review SLA

- First response within **24 hours**
- Approvals within **48 hours**
- Use GitHub comments for feedback
- Escalate stalled reviews via Teams or direct ping

---

## 🔀 Merge Policy

- **Squash merge** into `main`
- CI must pass before merging
- At least **1 approval** required
- Stale approvals are dismissed on new commits

---

Let us know if you have questions or suggestions by opening an issue or contacting a maintainer.