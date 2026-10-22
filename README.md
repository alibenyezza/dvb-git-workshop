# Builders Wall · Git & GitHub Workshop

[![deploy](https://github.com/alibenyezza/dvb-git-workshop/actions/workflows/deploy.yml/badge.svg)](https://github.com/alibenyezza/dvb-git-workshop/actions/workflows/deploy.yml)

> **From first commit to deployment** — the exercise repo of the Git & GitHub workshop by **DeVinci Blockchain**
> (Thursday 22 October 2026, IIM – Digital School, Nanterre).

Tonight you will do what professional teams do every day: **fork** a project, create a **branch**,
make a **commit**, open a **Pull Request**, pass an **automatic check**… and see your work **deployed online**.

The project: a wall of participants, the **Builders Wall**. Your card (your GitHub avatar, your first name, your school,
an emoji and a message) shows up on the site as soon as your Pull Request is merged.

🌐 **The live wall:** https://alibenyezza.github.io/dvb-git-workshop/

📚 **After the workshop:** the slides, the cheat sheet and the documentation for every part → [resources/](resources/)

```
fork → clone → branch → your card → commit → push → Pull Request → ✅ check → merge → 🚀 live
```

---

## Contents

- [0. Before you start](#0-before-you-start)
- [Level 1 — Git on your laptop](#level-1--git-on-your-laptop-20-min)
- [Level 2 — Your card on the wall](#level-2--your-card-on-the-wall-25-min)
- [Plan B — no terminal](#plan-b--no-terminal)
- [Level 3 — Bonus](#level-3--bonus)
- [FAQ — the usual errors](#faq--the-usual-errors)
- [How it works](#how-it-works)

---

## 0. Before you start

You need:

| What | Where | Check |
|---|---|---|
| **Git** | https://git-scm.com/downloads (Windows: keep the default options) | `git --version` |
| **A GitHub account** | https://github.com/signup | you can log in |
| **VS Code** (recommended) | https://code.visualstudio.com | `code --version` |

> **Windows:** for the commands in this guide, open **Git Bash** (installed with Git) or the VS Code terminal.

Tell Git who you are (once per computer):

```bash
git config --global user.name "First Last"
git config --global user.email "you@example.com"     # the same email as on GitHub
git config --global init.defaultBranch main
git config --global core.editor "code --wait"         # VS Code as the editor instead of vim
```

Check: `git config --global --list`

---

## Level 1 — Git on your laptop (20 min)

Goal: understand **commit**, **branch** and **merge**… and create a **conflict** on purpose to learn how to fix it.
Everything happens on your laptop, in a new folder (not inside this repo).

```bash
# 1. Create a repo
mkdir my-first-repo
cd my-first-repo
git init -b main
code .                  # create README.md in VS Code with the line: # Hello DVB
```

```bash
# 2. First commit
git status                       # README.md is "untracked"
git add README.md                # → staging area
git commit -m "first commit"     # → a snapshot of your project
git log --oneline
```

```bash
# 3. A branch
git switch -c feature/bio
# in VS Code, add a line to README.md:  I do dev.   → save
git add README.md
git commit -m "feat: add my bio"
git switch main                  # the line disappears: it only exists on the branch
git merge feature/bio
git log --oneline --graph --all
```

**Now the conflict (on purpose!)** — two branches change the same line:

```bash
# on main: replace "I do dev." with "I do design."  → save
git commit -am "feat: bio design"
git switch feature/bio
# on feature/bio: replace the same line with "I do dev, really."  → save
git commit -am "feat: bio dev"
git switch main
git merge feature/bio            # → CONFLICT
```

Git prints `CONFLICT (content): Merge conflict in README.md`. Open `README.md`:

```text
# Hello DVB
<<<<<<< HEAD
I do design.
=======
I do dev, really.
>>>>>>> feature/bio
```

Keep the version you want (or both), **delete the 3 marker lines** `<<<<<<<`, `=======`, `>>>>>>>`, then:

```bash
git add README.md
git commit -m "fix: resolve bio conflict"
git log --oneline --graph --all   # admire your graph 🌳
```

> In VS Code, *Accept Current / Accept Incoming / Accept Both* buttons appear above the conflict.
> Panicking? `git merge --abort` cancels the merge and puts everything back.

---

## Level 2 — Your card on the wall (25 min)

Everywhere below, replace `<your-username>` with **your GitHub username in lowercase** (e.g. `ada-lovelace`).

### 1. Fork

Top right of this page: **Fork → Create fork**.
You get your own copy: `https://github.com/<your-username>/dvb-git-workshop`.

### 2. Clone **your** fork

```bash
git clone https://github.com/<your-username>/dvb-git-workshop.git
cd dvb-git-workshop
```

> ⚠️ Make sure you clone **your fork** (your username in the URL), not the original repo: otherwise `push` will be refused (error 403).

### 3. Create your branch

```bash
git switch -c add/<your-username>
```

### 4. Create your card

```bash
cp builders/_template.json builders/<your-username>.json
code builders/<your-username>.json
```

Change the values (keep the quotes and the commas):

```json
{
  "github": "<your-username>",
  "name": "Ada L.",
  "school": "IIM",
  "role": "Dev",
  "emoji": "🚀",
  "message": "My first commit!"
}
```

| Field | Rule |
|---|---|
| `github` | your GitHub username in lowercase, **identical to the file name** |
| `name` | 30 characters max |
| `school` | 20 characters max |
| `role` | exactly one of: `Dev`, `Design`, `Data`, `Product`, `Business`, `Curious` |
| `emoji` | **one single** emoji |
| `message` | 80 characters max, no links, no HTML |

You can test it before sending (if you have Node.js): `node scripts/validate.mjs`

### 5. Commit & push

```bash
git status
git add builders/<your-username>.json
git commit -m "feat: add <your-username> to the wall"
git push -u origin add/<your-username>
```

> First `push`: a window opens so you can log in to GitHub. Log in and you are done.
> If the terminal asks you for a password, see the [FAQ](#faq--the-usual-errors).

### 6. Open the Pull Request

On your fork's page, GitHub shows a **Compare & pull request** banner → click it.
Check that the PR goes **from** `<your-username>/dvb-git-workshop` · `add/<your-username>` **to** `alibenyezza/dvb-git-workshop` · `main`,
tick the checklist, then **Create pull request**.

### 7. Wait for the check ✅

The **validate** check verifies your card automatically (≈ 20 s).
- ✅ green: perfect, the host will merge it.
- ❌ red: click **Details**, read the message, fix your file, then `git commit -am "fix: my card"` and `git push`. The PR updates itself.

> If the check says *"Waiting for approval"*, that is normal for a first contribution: the host approves it.

### 8. Merge → live 🚀

Once your PR is merged, GitHub Actions builds and deploys the site (≈ 1 min).
Your card appears on **https://alibenyezza.github.io/dvb-git-workshop/** (the wall refreshes by itself every 20 s).

---

## Plan B — no terminal

Git does not work on your laptop? You can still go through a real Pull Request, directly on GitHub:

1. Open the [`builders/`](builders/) folder of this repo.
2. **Add file → Create new file**.
3. File name: `<your-username>.json`, paste the content of the template and edit it.
4. **Commit changes…** → GitHub offers to create a fork and a branch for you: accept.
5. **Propose changes → Create pull request**.

You did exactly the same thing as with the terminal: fork, branch, commit, PR.

---

## Level 3 — Bonus

Done early? Pick a challenge:

1. **Review a PR** — open a neighbour's PR → **Files changed** tab → comment on a line → **Review changes → Approve**.
2. **Put your Level 1 repo on GitHub**:
   ```bash
   cd my-first-repo
   # create an empty repo "my-first-repo" on https://github.com/new (no README), then:
   git remote add origin https://github.com/<your-username>/my-first-repo.git
   git push -u origin main
   ```
3. **Your first release**, in your own repo:
   ```bash
   git tag -a v0.1.0 -m "First version"
   git push origin v0.1.0
   ```
   Then on GitHub: **Releases → Draft a new release** → pick `v0.1.0`.
4. **A real conflict** — edit your card on GitHub (✏️ icon) *and* locally, then `git pull`: fix the conflict like in Level 1.
5. **Open an issue** on this repo: an idea to improve the wall? **Issues → New issue**.

---

## FAQ — the usual errors

<details>
<summary><b><code>Author identity unknown</code> / <code>Please tell me who you are</code></b></summary>

Git does not know who you are:

```bash
git config --global user.name "First Last"
git config --global user.email "you@example.com"
```
Then run your `git commit` again.
</details>

<details>
<summary><b><code>Permission to alibenyezza/dvb-git-workshop.git denied</code> (403)</b></summary>

You cloned the original repo instead of **your fork**. Fork the repo (**Fork** button), then:

```bash
git remote set-url origin https://github.com/<your-username>/dvb-git-workshop.git
git remote -v        # check: your username must appear
git push -u origin add/<your-username>
```
</details>

<details>
<summary><b><code>! [rejected] … (fetch first)</code> or <code>(non-fast-forward)</code></b></summary>

Your branch on GitHub has a commit you do not have locally (maybe you edited a file on the website):

```bash
git pull --rebase origin add/<your-username>
git push
```
</details>

<details>
<summary><b>The terminal asks me for a <code>Username</code> / <code>Password</code></b></summary>

GitHub no longer accepts passwords in the terminal. The easiest fix: install the **GitHub CLI** (https://cli.github.com), then

```bash
gh auth login        # pick GitHub.com → HTTPS → Login with a web browser
gh auth setup-git
```
On Windows, Git normally installs *Git Credential Manager*, which opens a login window by itself.
</details>

<details>
<summary><b>The <code>validate</code> check is red ❌</b></summary>

In your PR: **Checks** (or **Details** next to the ❌) → open the *Check the cards* step. The message tells you which file is wrong and how to fix it, for example:

```text
  builders/ada-lovelace.json
    ✗ "role": "Developer" is not in the list
    → pick exactly one of: Dev, Design, Data, Product, Business, Curious
```
Fix it, then `git commit -am "fix: my card"` and `git push`.
</details>

<details>
<summary><b>I am stuck in a weird screen (vim) after <code>git commit</code></b></summary>

You forgot `-m "message"` and Git opened the **vim** editor. To get out:
- type your message, then `Esc` → `:wq` → `Enter` (save and quit);
- or `Esc` → `:q!` → `Enter` (quit without doing anything).

To never end up there again: `git config --global core.editor "code --wait"`.
</details>

<details>
<summary><b><code>error: src refspec add/… does not match any</code></b></summary>

You have not committed anything on this branch yet, or the branch name is different. Check with `git status` and `git branch`, make your `git commit`, then push again.
</details>

<details>
<summary><b>My fork is behind the original repo</b></summary>

On your fork's page: **Sync fork → Update branch**. Or from the command line:

```bash
git remote add upstream https://github.com/alibenyezza/dvb-git-workshop.git
git switch main
git pull upstream main
```
</details>

<details>
<summary><b>My PR is merged but my card does not show up</b></summary>

Deployment takes about 1 minute (**Actions** tab of the original repo), then the wall refreshes every 20 s. If you still see nothing, reload the page with `Ctrl+F5`.
</details>

---

## How it works

```
builders/*.json ──► PR ──► .github/workflows/check.yml  (validate: checks the cards)
                    │
                  merge
                    ▼
               main ──► .github/workflows/deploy.yml (validate → build → GitHub Pages)
                                    │
                                    ▼
                    _site/index.html + builders.json  →  the live wall
```

| File | Role |
|---|---|
| `builders/` | one JSON card per participant |
| `scripts/validate.mjs` | checks the cards (Node 20, no dependencies) |
| `scripts/build.mjs` | generates the site in `_site/` |
| `site/` | the wall page (HTML/CSS/JS) |
| `.github/workflows/` | the GitHub Actions: `check` on PRs, `deploy` on `main` |

Test locally:

```bash
node scripts/validate.mjs
node scripts/build.mjs
python -m http.server 8000 --directory _site   # then open http://localhost:8000
```

---

Made with 💙 by **DeVinci Blockchain**. MIT licence.
