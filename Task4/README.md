# Task 4 – Git Version Control and GitHub Workflow

## 📌 Objective

To manage a DevOps project using Git and GitHub best practices.

This task demonstrates a complete Git workflow including:

- Repository initialization
- Branch creation
- Feature development
- Commits
- Pull requests
- Branch merging
- Git tags
- `.gitignore`
- Markdown documentation

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Git | Version control |
| GitHub | Remote repository and collaboration |
| GitHub Pull Request | Code review and merging |
| Markdown | Project documentation |

---

## 🌿 Branching Strategy

The project follows a simple three-level branching workflow:

```text
                    main
                      │
                      ▼
                     dev
                      │
                      ▼
               feature/task4
```

### Branches

| Branch | Purpose |
|---|---|
| `main` | Stable and final version |
| `dev` | Development and integration |
| `feature/task4` | Development of Task 4 changes |

---

## 🔄 Git Workflow

```text
Create Feature Branch
        │
        ▼
   Make Changes
        │
        ▼
      Commit
        │
        ▼
 Push Feature Branch
        │
        ▼
  Pull Request → dev
        │
        ▼
      Review
        │
        ▼
      Merge
        │
        ▼
  Pull Request → main
        │
        ▼
      Merge
        │
        ▼
    Git Tag v1.0.0
```

---

## 📚 Git Concepts Demonstrated

### 1. Repository Initialization

A Git repository is initialized using:

```bash
git init
```

### 2. Branching

Branches are used to develop features independently without directly modifying the stable `main` branch.

```bash
git branch dev
git switch dev
```

A feature branch is created using:

```bash
git switch -c feature/task4
```

### 3. Committing Changes

Changes are staged and committed using:

```bash
git add .
git commit -m "Add Task 4 documentation"
```

### 4. Pushing Changes

The feature branch can be pushed to GitHub using:

```bash
git push -u origin feature/task4
```

### 5. Pull Requests

A Pull Request is created on GitHub to review and merge changes from the feature branch into `dev`.

```text
feature/task4
       │
       ▼
 Pull Request
       │
       ▼
      dev
```

After development is completed, another Pull Request can be created from `dev` into `main`.

```text
dev
 │
 ▼
Pull Request
 │
 ▼
main
```

### 6. Git Tags

Git tags are used to mark important versions of the project.

Example:

```bash
git tag -a v1.0.0 -m "Task 4 version 1.0.0"
git push origin v1.0.0
```

---

# 🎓 Interview Questions and Answers

## 1. What is Git?

Git is a distributed version control system used to track changes in files and manage different versions of a project.

It allows developers to work on different branches and maintain the history of project changes.

---

## 2. What is the difference between merge and rebase?

### Merge

`git merge` combines the changes from one branch into another branch while preserving the existing branch history.

Example:

```bash
git switch main
git merge dev
```

### Rebase

`git rebase` moves the commits of one branch on top of another branch, creating a more linear history.

Example:

```bash
git switch feature/task4
git rebase dev
```

### Difference

| Merge | Rebase |
|---|---|
| Preserves branch history | Creates a more linear history |
| May create a merge commit | Usually avoids a merge commit |
| Safer for shared branches | Should be used carefully on shared branches |

---

## 3. What is a Pull Request?

A Pull Request (PR) is a request to merge changes from one branch into another branch.

Pull Requests allow developers to:

- Review code
- Discuss changes
- Identify issues
- Run automated checks
- Approve changes
- Merge the code

Example:

```text
feature/task4
       │
       ▼
 Pull Request
       │
       ▼
      dev
```

---

## 4. How do you resolve merge conflicts?

A merge conflict occurs when Git cannot automatically combine changes from different branches.

The general process is:

```text
Identify the conflict
        │
        ▼
Open the conflicting file
        │
        ▼
Choose the required changes
        │
        ▼
Remove conflict markers
        │
        ▼
Save the file
        │
        ▼
git add .
        │
        ▼
git commit
```

Useful commands:

```bash
git status
git add .
git commit -m "Resolve merge conflict"
```

---

## 5. What are Git tags?

Git tags are references used to mark specific commits in the repository history.

They are commonly used to identify releases or important versions.

Example:

```bash
git tag -a v1.0.0 -m "Task 4 version 1.0.0"
```

Push the tag to GitHub:

```bash
git push origin v1.0.0
```

---

## 6. What is Git workflow?

Git workflow is the process used to manage changes in a project using Git.

A typical workflow is:

```text
Create Branch
     │
     ▼
Make Changes
     │
     ▼
Commit
     │
     ▼
Push
     │
     ▼
Pull Request
     │
     ▼
Code Review
     │
     ▼
Merge
```

The workflow used in this task is:

```text
feature/task4
       │
       ▼
      dev
       │
       ▼
      main
```

---

## 7. Explain git stash.

`git stash` temporarily stores uncommitted changes without creating a commit.

It is useful when you need to switch branches while keeping your unfinished work.

Save changes:

```bash
git stash
```

Restore the changes:

```bash
git stash pop
```

---

## 8. What is the use of `.gitignore`?

`.gitignore` specifies files and directories that Git should not track.

Examples include:

```text
.env
*.log
node_modules/
.vscode/
```

It helps prevent unnecessary, temporary, generated, or sensitive files from being committed to the repository.

---

# 🎯 Task Deliverables

The following deliverables are included in this task:

- Git repository
- GitHub repository
- `main` branch
- `dev` branch
- Feature branch
- Proper Git commits
- Pull Requests
- Branch merging
- `.gitignore`
- Git tag
- Markdown documentation
- README.md

---

# 🎉 Outcome

This task provides practical experience with:

- Git version control
- Branch management
- Feature-based development
- Commit management
- Pull Request workflow
- Branch merging
- Git tags
- `.gitignore`
- GitHub collaboration

---

## ✅ Task 4 Completed

**Git Version Control and GitHub Workflow**