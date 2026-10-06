\# Task 4 – Git Version Control and GitHub Workflow



\## 📌 Objective



To manage a DevOps project using Git and GitHub best practices.



This task demonstrates:



\- Git repository management

\- Branching

\- Feature development

\- Pull requests

\- Merging

\- Git tags

\- `.gitignore`

\- Markdown documentation

\- Git workflow



\---



\## 🛠️ Tools Used



| Tool | Purpose |

|---|---|

| Git | Version control |

| GitHub | Remote repository |

| GitHub Pull Request | Code review and merging |

| Markdown | Documentation |



\---



\## 🌿 Branching Strategy



This task uses three types of branches:



```text

main

&#x20; │

&#x20; └── dev

&#x20;      │

&#x20;      └── feature/task4

```



\- \*\*main\*\* – Stable version of the project

\- \*\*dev\*\* – Development and integration branch

\- \*\*feature/task4\*\* – Feature development branch



\---



\## 🔄 Git Workflow



```text

Feature Branch

&#x20;     ↓

&#x20;   Commit

&#x20;     ↓

&#x20;Push to GitHub

&#x20;     ↓

&#x20;Pull Request

&#x20;     ↓

&#x20;    dev

&#x20;     ↓

&#x20;Pull Request

&#x20;     ↓

&#x20;   main

&#x20;     ↓

&#x20;  Git Tag

```



\---



\## 📚 Topics Covered



1\. Git repository initialization

2\. Git branches

3\. Feature branches

4\. Git commits

5\. Pull requests

6\. Branch merging

7\. Merge conflicts

8\. Git tags

9\. Git stash

10\. `.gitignore`



\---



\# 🎓 Interview Questions and Answers



\## 1. What is Git?



Git is a distributed version control system used to track changes in source code and manage different versions of a project.



It allows multiple developers to work on the same project and maintains the complete history of changes.



\---



\## 2. What is the difference between merge and rebase?



\### Merge



`git merge` combines the changes from one branch into another branch while preserving the existing branch history.



Example:



```bash

git switch main

git merge dev

```



\### Rebase



`git rebase` moves the commits of one branch on top of another branch, creating a more linear history.



Example:



```bash

git switch feature/task4

git rebase dev

```



\### Difference



| Merge | Rebase |

|---|---|

| Preserves branch history | Creates a more linear history |

| Can create a merge commit | Usually avoids a merge commit |

| Safer for shared branches | Should be used carefully on shared branches |



\---



\## 3. What is a Pull Request?



A Pull Request (PR) is a request to merge changes from one branch into another branch.



It allows developers to:



\- Review code

\- Discuss changes

\- Identify problems

\- Run automated checks

\- Approve changes

\- Merge changes



Example:



```text

feature/task4

&#x20;     ↓

Pull Request

&#x20;     ↓

&#x20;    dev

```



\---



\## 4. How do you resolve merge conflicts?



A merge conflict occurs when Git cannot automatically combine changes from two branches.



The general process is:



```text

Identify the conflict

&#x20;       ↓

Open the conflicting file

&#x20;       ↓

Choose the correct changes

&#x20;       ↓

Remove conflict markers

&#x20;       ↓

Save the file

&#x20;       ↓

git add .

&#x20;       ↓

git commit

```



Example:



```bash

git status

git add .

git commit -m "Resolve merge conflict"

```



\---



\## 5. What are Git tags?



Git tags are references used to mark specific commits in the repository history.



They are commonly used to identify software releases or important versions.



Example:



```bash

git tag -a v1.0.0 -m "Task 4 version 1.0.0"

```



Push the tag to GitHub:



```bash

git push origin v1.0.0

```



\---



\## 6. What is Git workflow?



Git workflow is the process used to manage changes in a project using Git.



A typical workflow is:



```text

Create Branch

&#x20;    ↓

Make Changes

&#x20;    ↓

Commit

&#x20;    ↓

Push

&#x20;    ↓

Pull Request

&#x20;    ↓

Code Review

&#x20;    ↓

Merge

```



In this task:



```text

feature/task4

&#x20;     ↓

&#x20;    dev

&#x20;     ↓

&#x20;   main

```



\---



\## 7. Explain git stash.



`git stash` temporarily stores uncommitted changes without creating a commit.



It is useful when you need to switch branches but are not ready to commit your current work.



Example:



```bash

git stash

```



To restore the changes:



```bash

git stash pop

```



\---



\## 8. What is the use of `.gitignore`?



`.gitignore` is a file that specifies files and directories that Git should not track.



For example:



```text

.env

\*.log

node\_modules/

.vscode/

```



This prevents unnecessary or sensitive files from being committed to the repository.



\---



\## 🎯 Task Deliverables



\- Git repository

\- GitHub repository

\- Main branch

\- Development branch

\- Feature branch

\- Proper commits

\- Pull requests

\- Branch merging

\- `.gitignore`

\- Git tag

\- Markdown documentation

\- README.md



\---



\## 🎉 Outcome



This task provides practical experience with:



\- Git version control

\- Branch management

\- Feature-based development

\- Pull request workflow

\- Code merging

\- Git tags

\- `.gitignore`

\- GitHub collaboration



\### Task 4 – Git Version Control and GitHub Workflow: Completed ✅

