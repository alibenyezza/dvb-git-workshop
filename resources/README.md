# 📚 Resources · Git & GitHub Workshop

> Thursday 22 October 2026 · IIM – Digital School, Nanterre · by **DeVinci Blockchain**
> *From first commit to deployment.*

Thanks for coming! Everything we saw together is here, with the official documentation for each part so you can go further at your own pace.

| | |
|---|---|
| 🖥️ **The slides** | [slides.pdf](slides.pdf) (27 slides) |
| 📄 **The Git & GitHub cheat sheet** | [cheatsheet.pdf](cheatsheet.pdf) (3 pages: every command, then videos, games, docs and certification) |
| ⚙️ **The CI/CD & GitHub Actions cheat sheet** | [cicd-cheatsheet.pdf](cicd-cheatsheet.pdf) (2 pages: pipelines, workflow syntax, security, videos, courses, certifications) |
| 🧱 **The Builders Wall** | https://alibenyezza.github.io/dvb-git-workshop/ |
| 🛠️ **The exercise guide** | [README of the repo](../README.md) (Lab 1, Lab 2, plan B, FAQ of the usual errors) |

---

## The workshop, part by part

### 1 · Git vs GitHub
Git is the tool that runs on your computer, even offline, and keeps the full history of your project. GitHub hosts your Git projects online and adds collaboration: Pull Requests, reviews, automation.
- 📖 [What is Git? (Pro Git, chapter 1)](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)
- 📖 [About GitHub and Git](https://docs.github.com/en/get-started/start-your-journey/about-github-and-git)

### 2 · The 4 areas and the commit
Working directory → `git add` → staging area → `git commit` → local repo → `git push` → remote (GitHub). A commit is a snapshot of the project with an ID (hash), an author, a date and a message.
- 📖 [Recording changes to the repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
- 📖 [Viewing the commit history](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

### 3 · Branches
One branch per task, and `main` stays clean. `git switch -c feature/x` creates a branch, `git merge` brings it back.
- 📖 [Git branching in a nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
- 🎮 [Learn Git Branching](https://learngitbranching.js.org/): an interactive game, the best way to really understand branches

### 4 · Branches in real teams
`main` = production, `staging` = pre-production tests, `dev` = integration, then short branches named `feature/`, `fix/`, `hotfix/`, `release/`. Two schools: **Git Flow** (big teams, planned releases) and **trunk-based** (main + short branches, most startups).
- 📖 [Branching workflows (Pro Git)](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- 📖 [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow)
- 📖 [Trunk-based development](https://trunkbaseddevelopment.com/)

### 5 · Lab 1: your first repo
`git init`, `add`, `commit`, `switch -c`, `merge`, `log --oneline --graph --all`: all the commands are in the [cheat sheet](cheatsheet.pdf) and in [Level 1 of the guide](../README.md#level-1--git-on-your-laptop).

> 🔒 **Your email is visible in your commits.** On a public repo, anyone can read the email from your `git config`. To hide it in future commits, use your GitHub *noreply* address: [Setting your commit email address](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address).

### 6 · Merge conflicts
Two branches changed the same line: Git asks you to choose. Open the file, keep the right version, delete the markers `<<<<<<<` `=======` `>>>>>>>`, then `git add` and `git commit`. Panic button: `git merge --abort`.
- 📖 [Basic merge conflicts (Pro Git)](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging#_basic_merge_conflicts)
- 📖 [Resolving a merge conflict on GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-on-github)
- 📖 [Merge conflicts in VS Code](https://code.visualstudio.com/docs/sourcecontrol/merge-conflicts)

### 7 · Writing good commits
`type: what the commit does`: `feat:`, `fix:`, `docs:`, `refactor:`, `chore:`… Never `update` or `fix stuff`: your history is what recruiters look at.
- 📖 [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

### 8 · Versions & tags
`v1.4.2` = MAJOR.MINOR.PATCH. `git tag -a v1.0.0 -m "First release"` then `git push origin v1.0.0`, and on GitHub it becomes a Release.
- 📖 [Semantic Versioning](https://semver.org/)
- 📖 [Tagging (Pro Git)](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- 📖 [Managing releases on GitHub](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository)

### 9 · Lab 2: fork & Pull Request
**Fork** = your copy on GitHub · **clone** = that copy on your laptop · **push** = send your commits to your fork · **Pull Request** = ask the original project to take your change · **merge** = it's in.
- 📖 [Fork a repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)
- 📖 [Creating a pull request from a fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork)
- 📖 [Syncing your fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork) (to get everyone's cards in your copy: **Sync fork** button on GitHub, then `git pull`)
- 📖 [Contributing to open source](https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project)

### 10 · CI/CD: how the wall got deployed
Merge into `main` → **GitHub Actions** runs the workflow → checks every card and builds the site → **GitHub Pages** publishes it. Nobody touched the website by hand. The workflows of this repo are in [`.github/workflows/`](../.github/workflows/).
- 📖 [Understanding GitHub Actions](https://docs.github.com/en/actions/about-github-actions/understanding-github-actions)
- 📖 [GitHub Pages quickstart](https://docs.github.com/en/pages/quickstart)
- 📖 [Using custom workflows with GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)

### 11 · Protecting `main`
No change reaches `main` without a Pull Request and a green check, and nobody can rewrite its history. That's why a direct `git push origin main` is refused.
- 📖 [About rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)
- 📖 [About protected branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)

---

## Practise at home: the bonus challenges

1. **Update your card**: new branch, change your message, new Pull Request.
2. **Review someone's PR** and leave a constructive comment.
3. **Undo a commit** without rewriting history: `git revert <hash>`.
4. **Explore the history**: `git log --graph --oneline --all`, `git blame README.md`.
5. **Try rebasing** on your own repo: `git rebase main` (never on a shared branch).
6. **Put your portfolio online**: create a repo named `your-username.github.io` and turn on GitHub Pages ([guide](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)).
7. **Create a conflict on purpose** in your Lab 1 repo and resolve it in VS Code.

## Keep learning Git & GitHub

Page 3 of the [cheat sheet](cheatsheet.pdf) gathers all of this. The links:

**🎬 Watch**
- [Git Explained in 100 Seconds](https://www.youtube.com/watch?v=hwP7WQkmECE) · Fireship · the big picture in 2 minutes
- [How Git Works: Explained in 4 Minutes](https://www.youtube.com/watch?v=e9lnsKot_SQ) · ByteByteGo · the 4 areas, visually
- [Git and GitHub for Beginners, Crash Course](https://www.youtube.com/watch?v=RGOj5yH7evk) · freeCodeCamp · everything we did at the workshop
- [Git Tutorial for Beginners: Learn Git in 1 Hour](https://www.youtube.com/watch?v=8JJ101D3knE) · Programming with Mosh
- [Git & GitHub Crash Course For Beginners](https://www.youtube.com/watch?v=SWYqp7iY_Tc) · Traversy Media
- [Git and GitHub Tutorial for Beginners](https://www.youtube.com/watch?v=tRZGeaHPoaw) · Kevin Stratvert · with VS Code and GitHub Desktop
- [Version Control (git)](https://www.youtube.com/watch?v=2sjqTHE0zok) · MIT Missing Semester · how Git works inside
- [Git for Professionals](https://www.youtube.com/watch?v=Uszj_k0DGsg) · freeCodeCamp · rebase, cherry-pick, reflog, branching strategies
- [13 Advanced (but useful) Git Techniques and Shortcuts](https://www.youtube.com/watch?v=ecK3EnyGD8o) · Fireship

**🎮 Play & visualise (free)**
- [Learn Git Branching](https://learngitbranching.js.org/) · [Oh My Git!](https://ohmygit.org/) (a card game) · [Visualizing Git](https://git-school.github.io/visualizing-git/)

**🧪 Learn by doing (free)**
- [GitHub Skills](https://skills.github.com/): [Introduction to GitHub](https://github.com/skills/introduction-to-github), [Review pull requests](https://github.com/skills/review-pull-requests), [Resolve merge conflicts](https://github.com/skills/resolve-merge-conflicts)
- [First Contributions](https://github.com/firstcontributions/first-contributions): your first open-source PR, guided · [Good First Issue](https://goodfirstissue.dev/): beginner-friendly issues in real projects

**📖 Read**
- [Atlassian Git tutorials](https://www.atlassian.com/git/tutorials) · [Missing Semester: version control](https://missing.csail.mit.edu/2020/version-control/) · [Git reference](https://git-scm.com/docs)
- When things go wrong: [Oh Shit, Git!?!](https://ohshitgit.com/) · [Git Flight Rules](https://github.com/k88hudson/git-flight-rules)
- [GitHub's official Git cheat sheet](https://education.github.com/git-cheat-sheet-education.pdf)

**🧰 Tools**
- [VS Code Source Control](https://code.visualstudio.com/docs/sourcecontrol/overview) · [GitHub Desktop](https://desktop.github.com/) · [GitHub CLI](https://cli.github.com/)

## Go further with CI/CD & GitHub Actions

Everything is summed up in the [CI/CD & GitHub Actions cheat sheet](cicd-cheatsheet.pdf). The links:

**🎬 Watch**
- [GitHub Actions Tutorial: basic concepts and CI/CD pipeline with Docker](https://www.youtube.com/watch?v=R8_veQiYBjI) · TechWorld with Nana · 32 min
- [GitHub Actions: from Zero to Hero in 90 minutes](https://www.youtube.com/watch?v=TLB5MY9BBa4) · CoderDave · environments, secrets, runners
- [Complete GitHub Actions Course: from beginner to pro](https://www.youtube.com/watch?v=Xwpi0ITkL3U) · DevOps Directive
- [5 Ways to DevOps-ify your App](https://www.youtube.com/watch?v=eB0nUzAI7M8) · Fireship · short
- [GitHub Actions Certification: full course](https://www.freecodecamp.org/news/pass-the-github-actions-certification-exam/) · freeCodeCamp · ≈ 3 h, prep for the GH-200 exam

**🧪 Learn by doing (free)**
- [GitHub Skills](https://skills.github.com/): [Hello GitHub Actions](https://github.com/skills/hello-github-actions), [Test with Actions](https://github.com/skills/test-with-actions), [Reusable workflows](https://github.com/skills/reusable-workflows), [Publish packages](https://github.com/skills/publish-packages), [Write JavaScript actions](https://github.com/skills/write-javascript-actions)
- [Microsoft Learn: Automate your workflow with GitHub Actions](https://learn.microsoft.com/en-us/training/paths/automate-workflow-github-actions/) (official GH-200 learning path)
- [Microsoft Learn: GitHub Foundations](https://learn.microsoft.com/en-us/training/paths/github-foundations/) (official GH-900 learning path)

**📖 Docs**
- [Quickstart](https://docs.github.com/en/actions/writing-workflows/quickstart) · [Workflow syntax](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions) · [Events that trigger workflows](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows)
- [Secrets](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) · [Environments](https://docs.github.com/en/actions/deployment/targeting-different-environments/managing-environments-for-deployment) · [Matrix](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow) · [Caching](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/caching-dependencies-to-speed-up-workflows)
- [Security hardening for GitHub Actions](https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions)
- [Actions Marketplace](https://github.com/marketplace?type=actions) · [Starter workflows](https://github.com/actions/starter-workflows) · [Dependabot](https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates)
- Tools: [actionlint](https://rhysd.github.io/actionlint/) (finds errors in your workflows) · [act](https://github.com/nektos/act) (runs them locally)
- Concepts: [Continuous Integration, by Martin Fowler](https://martinfowler.com/articles/continuousIntegration.html) · [CI vs Continuous Delivery vs Continuous Deployment](https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment) · [DevOps roadmap](https://roadmap.sh/devops)

**🎓 Get certified**

| Exam | Certification | Level |
|---|---|---|
| GH-900 | [GitHub Foundations](https://learn.microsoft.com/en-us/credentials/certifications/github-foundations/) | Start here · **free for verified students** |
| GH-200 | [GitHub Actions](https://learn.microsoft.com/en-us/credentials/certifications/github-actions/) | Intermediate · CI/CD |
| GH-300 | [GitHub Copilot](https://learn.microsoft.com/en-us/credentials/certifications/github-copilot/) | AI-assisted coding |
| GH-500 | [GitHub Advanced Security](https://learn.microsoft.com/en-us/credentials/certifications/github-advanced-security/) | Secure code |
| GH-100 | [GitHub Administration](https://learn.microsoft.com/en-us/credentials/certifications/github-administration/) | Admins |

> **Students:** verify your status on [GitHub Education](https://education.github.com/pack), then claim a free GitHub Foundations voucher from the Student Developer Pack, while supplies last ([details](https://education.github.com/experiences/foundations_certificate)). Exams are booked on Microsoft Learn (Pearson VUE, online), and each certification page has a free practice assessment.

## Go further

- 🎓 [GitHub Student Developer Pack](https://education.github.com/pack): pro tools for free with your student email.
- 📗 [Pro Git](https://git-scm.com/book/en/v2): the official Git book, free online.
- 🧑‍🏫 [GitHub Skills](https://skills.github.com/): short hands-on courses, right inside GitHub.
- 📘 [GitHub Docs](https://docs.github.com/)
- 🆘 [Oh Shit, Git!?!](https://ohshitgit.com/): how to get out of the classic mistakes.
- 🎮 [Learn Git Branching](https://learngitbranching.js.org/)

---

Questions? Open an [issue](https://github.com/alibenyezza/dvb-git-workshop/issues) on this repo, or come and talk to us at the next **DeVinci Blockchain** event. See you soon! 🚀
