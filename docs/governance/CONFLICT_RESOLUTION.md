# Conflict Resolution – TechNinjas

This document records how merge conflicts are identified, resolved, and evidenced.

---

## 🔍 Identification
- Conflicts are detected during `git merge` or GitHub PR merge attempts.
- GitHub highlights conflicting files in the PR view.
- CI may fail due to unresolved conflicts.

---

## 🛠️ Resolution Process
1. **Pull latest `main`**
   ```bash
   git checkout main
   git pull origin main
   ```

2. Create and switch to a conflict branch
   ```bash
   git checkout -b conflict/<description>
   ```

3. Merge main into branch
   ```bash
   git merge main
   ```

4. Resolve conflicts manually
- Edit files to keep correct changes.
- Remove conflict markers (<<<<<<<, =======, >>>>>>>).
- Run tests locally to confirm resolution.


5. Commit resolution
   ```bash
   git add .
   git commit -m "Resolve merge conflict in <file>"
   ```
   

6. Push branch and open PR
   ```bash
   git push origin conflict/<description>
   ```



📸 Evidence
- Screenshot of conflict markers in VS Code.
- Screenshot of resolved file after cleanup.
- Link to conflict resolution PR in GitHub.

📝 Notes
- Conflicts are resolved collaboratively when multiple contributors are involved.
- Resolution PRs are labeled with governance: conflict-resolution.
- CI must pass before merge.

<!-- Added clarification for merge conflict resolution steps -->

<!-- Conflict resolved between governance-files and main -->

