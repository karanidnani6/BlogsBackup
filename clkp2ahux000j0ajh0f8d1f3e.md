---
title: "#Day10: Advance Git & GitHub for DevOps Engineers."
datePublished: Sun Jul 30 2023 06:29:56 GMT+0000 (Coordinated Universal Time)
cuid: clkp2ahux000j0ajh0f8d1f3e
slug: day10-advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690522392470/5bf0ffca-1411-4951-b792-867769d27ff3.jpeg
tags: github, git, devops, git-rebase, 90daysofdevops

---

🌿 All About Git Branching 🌿

Hey there! 👋 Today, we're going to explore the magical world of Git Branching! 🌳 If you're a developer or a tech-savvy person, chances are you've heard about Git, the super cool version control system that helps us manage our code changes. 🐙 But what's this "branching" thingy? Let's dive in and find out! 🏊‍♂️

### 🌟 Git Branching: What's It All About?

Imagine you're working on a project 🏗️, and you want to add a new feature or fix a pesky bug. Instead of changing the main code directly and potentially breaking things for others, Git branching lets you create a separate "branch" 🌳 where you can work on your changes safely. It's like having your own coding playground! 🎉

### 💡 Why Branching is Awesome?

Here's the beauty of it – while you're doing your thing on your branch, the main code (often called "master" or "main" branch) remains untouched. 🚀 That means others can continue working on the project, and when you're ready, you can merge your changes back into the main code like a pro! 🤝

### 🔙 Git Revert and Reset: The Magic Undo Buttons 🔙

Okay, sometimes things go a little haywire, and we make mistakes – it happens to the best of us! 😅 That's where Git's "revert" and "reset" come to the rescue! 🚑

🔄 Git Revert:

Picture this: you've committed some code changes, but later you realize they're causing trouble 🐞, and you want to undo those changes. The "git revert" command is your superhero! 🦸‍♂️ It creates a new commit that undoes the specific changes you want to get rid of. Your code is saved, and the day is saved! 🌟

⚠️ Caution: Revert creates a new commit, so your commit history stays intact. Just be clear about what you're reverting! 😉

🔙 Git Reset:

Now, let's say you want to go back in time 🕰️, eliminating one or more commits entirely. Git "reset" is here to make it happen! It's like a time machine that can take you to any commit you choose. 😮

⚠️ Caution: Reset is a bit more dangerous – it erases commits permanently! So, be extra careful and use it wisely! 🧐

### 🔄 What Is Git Rebase? 🔄

Oh boy, get ready for some advanced Git magic! 🧙‍♂️ Git rebase is like giving your branch a makeover! 💅 Imagine you've been working on your branch for a while, and in the meantime, some changes have been made to the main branch. 🔄

Instead of merging your branch with the main one right away, "git rebase" lets you move your changes to the tip of the main branch. 🚀 It's like you're reapplying your changes on top of the latest and greatest stuff! 😎 This can keep your commit history tidy and linear. 🧹

💡 Keep in mind: Rebase can be fantastic, but it can also cause confusion if used carelessly. Make sure you're aware of its implications, especially if you're collaborating with other developers. 🤝

### 🤝 What Is Git Merge? 🤝

Ah, the classic Git merge! 🤜🤛 It's like bringing all the cool kids together at the same table! 🕺💃 When you're done working on your branch and you're satisfied with your changes, it's time to merge it with the main branch. 🎉

Git merge takes the code from your branch and combines it with the main branch, creating a new "merge commit" that incorporates both sets of changes. 🌈 The result? Your changes are now part of the main codebase for everyone to enjoy! 🎊

🌟 Pro Tip: Keep in mind that sometimes merge conflicts may pop up when Git tries to combine the changes. Don't worry, though – you've got the skills to resolve them like a pro! 💪

That's a wrap on our Git adventure! 🎬 We've explored branching, the magic undo buttons (revert and reset), the transformative rebase, and the inclusive merge! 🌟 Git is an amazing tool that makes version control feel like a breeze! 🌬️ So go ahead, try it out, and unleash your coding powers! 🚀💻

Keep branching and keep coding! 🌳 Happy Git-ing! 😄✨

### Task 1:

Adding Features and Restoring Previous Versions

In this task, we'll learn how to create a new branch, add a file, and commit changes. We'll also make some additional commits and then restore the file to a previous version.

Step 1: Create a new branch and add a file

We start by creating a new branch called "dev" using the following command:

```plaintext
git checkout -b dev
```

Next, we create a text file called `version01.txt` inside the `Devops/Git/` directory with the content "This is the first feature of our application."

Step 2: Commit changes and push to the remote repository

We add and commit the changes made to the new branch with the commit message "Added new feature."

```plaintext
git add version01.txt
git commit -m "Added new feature"
```

To make these changes visible in the remote repository, we push the branch to the remote.

```plaintext
git push origin dev
```

Step 3: Add more commits to the dev branch

Now, we add new content to the `version01.txt` file as follows:

```plaintext
1st line>> This is the bug fix in development branch
```

Commit this change with the message "Added feature2 in development branch."

Then, add the second line to the file:

```plaintext
2nd line>> This is gadbad code
```

Commit this change with the message "Added feature3 in development branch."

Lastly, add the third line to the file:

```plaintext
3rd line>> This feature will gadbad everything from now.
```

Commit this change with the message "Added feature4 in development branch."

Step 4: Restore the file to a previous version

Suppose we want to revert the file to a previous version where the content was "This is the bug fix in development branch." To do this, we can use the `git reset` command:

```plaintext
Find the commit hash of the version you want to revert to
git log

# Reset to the commit hash of the version you want to revert to
git reset --hard <commit_hash>
```

### Task 2:

In this task, we'll explore the concept of branches with multiple branches, make changes to the dev branch, and then merge it into the master branch. Additionally, we'll try out Git rebase and observe the differences.

Step 1: Create and switch to the dev branch

We start by creating a new branch called "feature-branch" and switch to it.

```plaintext
git checkout -b feature-branch
```

Step 2: Make changes and commit in the dev branch

Here, we can make any desired changes to our files. For example, add new features or fix bugs.

```plaintext
Make changes and add files as necessary
git add .
git commit -m "Added new features in feature-branch"
```

Step 3: Merge the dev branch into the master branch

To incorporate the changes made in the dev branch into the master branch, we switch back to the master and merge the feature-branch.

```plaintext
git checkout master
git merge feature-branch
```

Step 4: Try Git rebase

Rebasing is another way to incorporate changes from one branch into another. It moves the entire feature-branch to begin on the tip of the master branch, resulting in a linear commit history.

```plaintext
# Assuming you are on the feature-branch
git rebase master
```

Conclusion 🏁:

In this blog, we covered two tasks that helped us understand the fundamental concepts of branching in Git. We learned how to create branches, commit changes, push to remote repositories, and perform basic operations like merging and reverting to previous versions. Git's branching and version control capabilities significantly enhance collaboration and productivity in software development, making it an essential tool for every developer. Remember, practice is the key to mastering Git, so don't hesitate to experiment and explore more about this powerful version control system. Happy coding! 🎉🚀