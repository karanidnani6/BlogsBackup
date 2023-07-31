---
title: "#Day11: Advance Git & GitHub for DevOps Engineers: Part-2"
datePublished: Mon Jul 31 2023 13:36:02 GMT+0000 (Coordinated Universal Time)
cuid: clkqwybrl000b09kz83byaxdo
slug: day11-advance-git-github-for-devops-engineers-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690790621635/04cbf59c-f21f-4d7b-80a6-cb9175704c93.png
tags: github, git, cherry-pick, git-stash, 90daysofdevops

---

Hey there! 👋 Welcome to another exciting blog about Git - the powerful version control system that developers love! Today, we're going to explore three important concepts that can make your Git journey smoother and more enjoyable: Git Stash, Cherry-pick, and Resolving Conflicts. Let's dive right in! 🏊‍♂️💨

### 🔹 Git Stash 🎒

Sometimes, when you're working on a project, you may need to switch to a different branch urgently, but you haven't completed your current changes yet. Don't worry; Git Stash comes to the rescue! 🦸‍♂️

Git Stash allows you to "stash" or temporarily store your current changes in a safe place, so you can quickly switch branches without committing them. Once you're back on the original branch, you can simply pop the stash and continue working where you left off. 🔄👌

### 🔹 Cherry-pick 🍒

Now, imagine a scenario where you worked on a new feature in one branch and committed it, but later you realized that the same change is also needed in another branch. Fear not, for Cherry-pick is here! 🍒🍴

Cherry-pick allows you to pick specific commits from one branch and apply them to another. It's like plucking the juicy cherry 🍒 from one tree and putting it on another! 🌳😉

### 🔹 Resolving Conflicts 🤝💔

Working in a team with Git is fantastic, but sometimes, different team members may make changes to the same file simultaneously, leading to conflicts. 😓 But don't panic; conflicts are normal and can be resolved easily! 💪🙂

When you attempt to merge or rebase branches with conflicting changes, Git will pause and notify you about the conflicts. It's your job as a developer to manually resolve these conflicts. The good news is that Git will guide you by marking the conflicting lines in the affected files. 🚀📝

To resolve conflicts, open the conflicting files in your code editor, look for the conflicting sections marked by Git, and make the necessary changes. Afterward, save the changes, commit them, and the conflict is resolved! 🎊🎈

Remember, effective communication within the team and staying updated with the project can minimize conflicts! 📞🗣️

### Task-01 :

* Create a new branch and make some changes to it.
    
* Use git stash to save the changes without committing them.
    
* Switch to a different branch, make some changes and commit them.
    
* Use git stash pop to bring the changes back and apply them on top of the new commits.
    

```bash
# Step 1: Create a new branch and make some changes to it.
git checkout -b new-feature
# Make some changes to the files.

# Step 2: Use git stash to save the changes without committing them.
git stash save "My changes on new-feature branch"

# Step 3: Switch to a different branch, make some changes, and commit them.
git checkout other-branch
# Make some changes to the files and commit them.

# Step 4: Use git stash pop to bring the changes back and apply them on top of the new commits.
git checkout new-feature
git stash pop
```

### Task-02 :

Adding features in the development branch and reflecting the commits in the Production branch using rebase.

Step 1: Switch to the development branch

```bash
git checkout development
```

Step 2: Open `version01.txt` and add the new lines as instructed.

```plaintext
This is the bug fix in development branch
Line2>> After bug fixing, this is the new feature with minor alteration”
```

Step 3: Commit the changes with message "Added feature2.1 in development branch"

```bash
git add version01.txt
git commit -m "Added feature2.1 in development branch"
```

Step 4: Add Line3&gt;&gt; This is the advancement of the previous feature

```bash
git add version01.txt
git commit -m "Added feature2.2 in development branch"
```

Step 5: Add Line4&gt;&gt; Feature 2 is completed and ready for release

```bash
git add version01.txt
git commit -m "Feature2 completed"
```

Now, you have completed all the commits with their respective messages in the development branch.

Step 6: Switch to the Production branch

```bash
git checkout Production
```

Step 7: Use rebase to apply the commits from the development branch to the Production branch

```bash
git rebase development
```

After performing the rebase, all the commits and their messages from the development branch will be reflected in the Production branch.

Remember, rebasing rewrites the commit history, so if these changes have already been pushed to a remote repository, you should be cautious about using rebase to avoid causing conflicts for other collaborators.

### Task 3 :

cherry-picking the commit "Added feature2.2 in development branch" into the Production branch and making the additional changes. Here's the step-by-step process:

Step 1: Switch to the Production branch

```plaintext
git checkout Production
```

Step 2: Cherry-pick the commit "Added feature2.2 in development branch"

```plaintext
git cherry-pick <commit-hash-of-"Added feature2.2 in development branch">
```

Step 3: Open `version01.txt` and add the following lines after "This is the advancement of the previous feature":

```plaintext
Line4>> Added few more changes to make it more optimized.
```

Step 4: Commit the changes with the message "Optimized the feature"

```plaintext
git add version01.txt
git commit -m "Optimized the feature"
```

Now, you have successfully cherry-picked the commit "Added feature2.2 in development branch" into the Production branch and made additional changes to optimize the feature. The changes are now committed with the message "Optimized the feature" in the Production branch. Your Production branch should be updated with these changes. 🚀