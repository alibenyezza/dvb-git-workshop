# 📚 Resources · Git & GitHub Workshop

> Thursday 22 October 2026 · IIM – Digital School, Nanterre · by **DeVinci Blockchain**
> *From first commit to deployment.*

Thanks for coming! Everything we saw together is here, with the official documentation for each part so you can go further at your own pace.

| | |
|---|---|
| 🖥️ **The slides** | [slides.pdf](slides.pdf) (27 slides) |
| 📄 **The cheat sheet** | [cheatsheet.pdf](cheatsheet.pdf) (2 pages, print it or keep it open while you code) |
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
`git init`, `add`, `commit`, `switch -c`, `merge`, `log --oneline --graph --all`: all the commands are in the [cheat sheet](cheatsheet.pdf) and in [Level 1 of the guide](../README.md#level-1--git-on-your-laptop-20-min).

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

## Go further

- 🎓 [GitHub Student Developer Pack](https://education.github.com/pack): pro tools for free with your student email.
- 📗 [Pro Git](https://git-scm.com/book/en/v2): the official Git book, free online.
- 🧑‍🏫 [GitHub Skills](https://skills.github.com/): short hands-on courses, right inside GitHub.
- 📘 [GitHub Docs](https://docs.github.com/)
- 🆘 [Oh Shit, Git!?!](https://ohshitgit.com/): how to get out of the classic mistakes.
- 🎮 [Learn Git Branching](https://learngitbranching.js.org/)

---

Questions? Open an [issue](https://github.com/alibenyezza/dvb-git-workshop/issues) on this repo, or come and talk to us at the next **DeVinci Blockchain** event. See you soon! 🚀
