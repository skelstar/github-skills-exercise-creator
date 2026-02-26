---
name: GitHub Skills Exercise
about: Template for creating a new GitHub Skills exercise
title: 'Git Fundamentals: Learn Version Control from Scratch'
labels: 'skills'
assignees: ''

---

# Logistics

- **Exercise Title:** Git Fundamentals: Learn Version Control from Scratch
- **Repo URL:** https://github.com/skills/git-fundamentals
- **Experience Level**: Beginner
- **Recommended Grouping**: Version Control Basics

### Relationships to other exercises

- **Previous Exercise:** None (this is an entry-level exercise)
- **Next Exercise:** Introduction to GitHub Flow

---

# Outline

## Story Plot

You've just joined a small team building a community recipe website. Before you can contribute code, you need to learn how your team tracks and manages changes using Git and GitHub. By the end of this exercise, you'll know how to save your work, create branches for new features, and propose your changes for review — the same workflow used by millions of developers worldwide.

## README

**Title:** Git Fundamentals: Learn Version Control from Scratch

Learn the core concepts of Git and version control by working directly inside GitHub. You'll create commits, work with branches, and merge your changes using the standard pull request workflow.

### Overview

1. Understand what version control is and why it matters.
1. Create your first commit by editing a file.
1. Create a branch to develop a new feature in isolation.
1. Open a pull request to propose your changes.
1. Merge your pull request to integrate changes into the main branch.

### What you will build

You'll contribute content to a simple recipe website by making commits on a feature branch and merging them through a pull request. Along the way you'll experience the full Git workflow that professional development teams use every day.

### Prerequisites

- A GitHub account (free).
- No prior version control or programming experience required.

---

## Step 1 - Understanding Commits

### Theory

**Version control** is a system that records changes to files over time so you can recall specific versions later. Git is the most widely used version control system in the world.

The fundamental unit of work in Git is a **commit** — a saved snapshot of your project at a point in time. Think of commits like checkpoints in a video game: you can always return to any checkpoint if something goes wrong.

Key concepts:

| Concept | Description |
|---------|-------------|
| **Repository (repo)** | The project folder tracked by Git, containing all files and their full history. |
| **Commit** | A snapshot of changes saved to the repository with a descriptive message. |
| **Commit message** | A short description of what changed and why, written by the author. |

Here is what a commit looks like on GitHub:

<img alt="Example commit on GitHub showing changed lines highlighted in green" src="(link)">

### References

- https://docs.github.com/en/get-started/using-git/about-git
- https://docs.github.com/en/get-started/start-your-journey/about-github-and-git

### Activity: Make Your First Commit

1. Open the repository and navigate to the `recipes/` folder.
1. Click `add-recipe.md` to open it in the file editor.
1. Add one line of text describing your favorite recipe.
1. Scroll down to the **Commit changes** section.
1. Write a short commit message (e.g., `Add my favorite recipe`).
1. Click **Commit changes** to save your snapshot.
1. Mona will check your work and share the next step!

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows#push) to the `main` branch with path `recipes/add-recipe.md`
- **Grading-Check:** Verify `recipes/add-recipe.md` was modified with at least one new line using [file-exists](https://github.com/skills/exercise-toolkit/tree/main/actions/file-exists) and a content check.

---

## Step 2 - Working with Branches

### Theory

A **branch** is an independent line of development within a repository. When you create a branch, you get a copy of the project at that moment. Changes you make on the branch do not affect the `main` branch until you merge them.

Branches let teams work on multiple features simultaneously without interfering with each other.

```
main       ──●──────────────────●──▶
               \               /
feature         ●──●──●──●──●
```

| Term | Description |
|------|-------------|
| `main` | The default branch — the stable, production-ready version. |
| **Feature branch** | A branch created to develop one specific feature or fix. |
| **HEAD** | A pointer to the commit you are currently viewing or working from. |

### References

- https://docs.github.com/en/get-started/using-git/about-branches
- https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches

### Activity: Create a Feature Branch

1. On the repository home page, click the **branch selector** dropdown (it shows `main`).
1. Type `add-my-recipe` in the text box.
1. Click **Create branch: add-my-recipe from main**.
1. You are now on your new branch — notice the branch name has changed in the dropdown.
1. Mona will detect the new branch and share the next step!

### Transition

- **Actions Trigger:** [`create`](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows#create) event (branch created)
- **Grading-Check:** Verify a branch named `add-my-recipe` exists in the repository.

---

## Step 3 - Making Changes on a Branch

### Theory

Now that you have a branch, you can make changes freely without affecting `main`. Each time you save a change, Git records a new commit on your branch, building up a history of the work you have done.

When you view a file on a branch, GitHub shows you the version on **that branch**, not `main`. This isolation is what makes branches so powerful — you can experiment safely.

A **diff** (short for difference) shows exactly what changed between two commits:

- Lines in **green** (prefixed with `+`) were added.
- Lines in **red** (prefixed with `-`) were removed.

<img alt="GitHub diff view showing added lines in green and removed lines in red" src="(link)">

### References

- https://docs.github.com/en/get-started/using-git/about-commits
- https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files

### Activity: Commit Changes to Your Branch

1. Make sure you are on the `add-my-recipe` branch (check the branch dropdown).
1. Navigate to `recipes/add-recipe.md`.
1. Click the pencil icon (✏️) to edit the file.
1. Add the name, ingredients, and steps for a recipe of your choice.
1. In **Commit changes**, write a descriptive message like `Add pasta recipe with ingredients and steps`.
1. Make sure **Commit directly to the `add-my-recipe` branch** is selected.
1. Click **Commit changes**.
1. Mona will review your branch and share the next step!

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows#push) with path `recipes/add-recipe.md` on branch `add-my-recipe`
- **Grading-Check:** Verify `recipes/add-recipe.md` on `add-my-recipe` branch contains more content than on `main`.

---

## Step 4 - Opening a Pull Request

### Theory

A **pull request (PR)** is a proposal to merge changes from one branch into another. It is the standard way to contribute changes in a collaborative project — even when working alone, pull requests create a clear record of what changed and why.

Pull requests let you and your teammates:

- Review the **diff** to see exactly what will change.
- Leave comments and suggestions on specific lines.
- Run automated checks before merging.
- Maintain a clear history of why decisions were made.

<img alt="GitHub pull request showing the Files Changed tab with a diff" src="(link)">

The lifecycle of a pull request:

1. **Open** — changes are proposed.
1. **Review** — collaborators examine the diff and leave feedback.
1. **Approve** — reviewers signal the changes are ready.
1. **Merge** — changes are integrated into the target branch.

### References

- https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests
- https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request

### Activity: Open a Pull Request

1. Go to the **Pull requests** tab of the repository.
1. Click **New pull request**.
1. Set **base** to `main` and **compare** to `add-my-recipe`.
1. Review the diff in the **Files changed** tab to confirm your recipe is shown.
1. Click **Create pull request**.
1. Add a title like `Add my recipe` and a short description of what you added.
1. Click **Create pull request** to submit it.
1. Mona will check your PR and share the next step!

### Transition

- **Actions Trigger:** [`pull_request`](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows#pull_request) with types `[opened, synchronize]`, base `main`, head `add-my-recipe`
- **Grading-Check:** Verify a pull request exists with base `main` and head `add-my-recipe`, and that it contains at least one commit modifying `recipes/add-recipe.md`.

---

## Step 5 - Merging and Viewing History

### Theory

When a pull request is **merged**, Git combines the commits from the feature branch into the target branch (`main`). After merging, the full history — including all commits from the branch — is permanently recorded in the repository.

You can explore this history at any time using the **Commits** view or the **Network graph** to understand how the project evolved.

```
main       ──●──────────────────●──▶  ← merge commit
               \               /
add-my-recipe   ●──●──●──●──●
```

Why history matters:

- You can see **who** changed **what** and **when**.
- You can **revert** to any past state if something breaks.
- You get a clear **audit trail** of all decisions made in the project.

### References

- https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/merging-a-pull-request
- https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-a-repositorys-network

### Activity: Merge Your Pull Request

1. Open your pull request from the **Pull requests** tab.
1. Scroll to the bottom and click **Merge pull request**.
1. Click **Confirm merge** to complete the merge.
1. Click **Delete branch** to tidy up the merged branch.
1. Navigate to the **Code** tab and open `recipes/add-recipe.md` — your recipe is now on `main`!
1. Click **N commits** (above the file list) to explore the commit history.
1. Mona will celebrate your success and share the review!

### Transition

- **Actions Trigger:** [`pull_request`](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows#pull_request) with type `closed` and `merged: true`
- **Grading-Check:** Verify the pull request was merged (not just closed) and that `recipes/add-recipe.md` on `main` contains the learner's recipe content.

---

## Review

In this exercise you experienced the complete Git workflow — from saving your first change all the way through merging a pull request. You now understand how professional teams track, review, and integrate code changes using Git and GitHub.

- Learned what version control is and why it matters.
- Created commits to save snapshots of your work.
- Used branches to develop features without affecting `main`.
- Opened a pull request to propose and review changes.
- Merged a pull request and explored the repository's commit history.

### What's next?

- https://docs.github.com/en/get-started/using-git
- https://skills.github.com (explore other GitHub Skills exercises)
- https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources

---

# Future Considerations

- Add a step covering `git clone` and working with a local Git client.
- Create a spin-off exercise focused on resolving merge conflicts.
- Consider a collaborative storyline where two learners work on the same file to illustrate merge conflicts naturally.
