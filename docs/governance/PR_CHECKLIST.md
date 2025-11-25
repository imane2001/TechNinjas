# Pull Request Checklist – TechNinjas

Before requesting a review, please confirm the following:

---

## ✅ General

- [ ] PR title is clear and descriptive
- [ ] Scope is ≤300 lines of code (LOC)
- [ ] Linked to relevant issue(s) and NFRs
- [ ] AI assistance disclosed in PR description (yes/no; what for)

---

## 🧪 Tests & Coverage

- [ ] Unit tests added or updated
- [ ] Coverage meets threshold (≥70%) if applicable
- [ ] All tests pass locally and in CI

---

## 📄 Documentation

- [ ] README or relevant docs updated
- [ ] Screenshots included for UI changes
- [ ] Code comments added where needed

---

## 🔒 Security & Secrets

- [ ] No secrets, keys, or credentials committed
- [ ] Secret scanning passes (if enabled)

---

## ⚙️ CI & Review

- [ ] CI checks are green
- [ ] Requested review from CODEOWNERS
- [ ] Responded to all review comments respectfully

---

## 🧹 Merge Readiness

- [ ] Rebased or merged with `main` if needed
- [ ] Ready for squash merge