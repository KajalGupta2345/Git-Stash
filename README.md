# Git Stash

## Introduction

`git stash` Git ka ek bahut useful command hai jo aapke **uncommitted changes ko temporarily save** kar deta hai, taaki aap bina commit kiye kisi aur branch ya task par kaam kar sakein.

Simple words me:

```text
Git Stash = Save Work Temporarily
```

Jab aapka kaam complete na hua ho aur achanak branch switch karni ho ya latest code pull karna ho, tab `git stash` use kiya jata hai.

---

# Why Use Git Stash?

Maan lo aap ek feature par kaam kar rahe ho:

```bash
git status
```

Output:

```text
modified: index.js
modified: app.js
```

Ab manager ne bola:

> "Pehle production bug fix karo."

Lekin aap apna current work commit nahi karna chahte.

Aise case me:

```bash
git stash
```

Use kar sakte ho.

---

# Basic Syntax

```bash
git stash
```

Ye command:

* Current changes save karti hai
* Working directory clean kar deti hai
* Last commit wali state restore kar deti hai

---

# Example

Before Stash:

```bash
git status
```

Output:

```text
modified: index.js
modified: app.js
```

Stash karo:

```bash
git stash
```

Output:

```text
Saved working directory and index state
```

Check:

```bash
git status
```

Output:

```text
nothing to commit, working tree clean
```

---

# View Stash List

Git multiple stashes save kar sakta hai.

Check karne ke liye:

```bash
git stash list
```

Example Output:

```text
stash@{0}: WIP on main
stash@{1}: WIP on login-feature
```

---

# Apply Stash

Saved changes wapas lane ke liye:

```bash
git stash apply
```

Ye latest stash ko restore karega.

---

# Apply Specific Stash

```bash
git stash apply stash@{1}
```

Specific stash restore ho jayega.

---

# Pop Stash

Most commonly used command:

```bash
git stash pop
```

Ye:

1. Stash apply karta hai
2. Stash list se remove bhi kar deta hai

Example:

```bash
git stash pop
```

---

# Difference Between Apply and Pop

| Command         | Restore Changes | Remove Stash |
| --------------- | --------------- | ------------ |
| git stash apply | Yes             | No           |
| git stash pop   | Yes             | Yes          |

---

# Save Stash With Message

Better practice:

```bash
git stash push -m "Working on login page"
```

Example:

```bash
git stash push -m "Navbar Design"
```

Check:

```bash
git stash list
```

Output:

```text
stash@{0}: On main: Navbar Design
```

---

# Show Stash Details

```bash
git stash show
```

Detailed changes:

```bash
git stash show -p
```

---

# Delete a Stash

Specific stash delete:

```bash
git stash drop stash@{0}
```

Example:

```bash
git stash drop stash@{1}
```

---

# Delete All Stashes

```bash
git stash clear
```

⚠️ Warning:

Ye saare stashes permanently delete kar deta hai.

---

# Stash Including Untracked Files

Normally stash sirf tracked files save karta hai.

Untracked files bhi save karne ke liye:

```bash
git stash -u
```

Ya:

```bash
git stash --include-untracked
```

---

# Real Workflow Example

### Working on Feature

```bash
git status
```

```text
modified: login.js
modified: style.css
```

### Save Work

```bash
git stash
```

### Switch Branch

```bash
git switch main
```

### Fix Bug

```bash
git add .
git commit -m "Fix navbar bug"
```

### Return to Feature Branch

```bash
git switch feature-login
```

### Restore Work

```bash
git stash pop
```

Ab saare changes wapas aa jayenge.

---

# Common Commands

```bash
# Save changes
git stash

# Save with message
git stash push -m "message"

# View stashes
git stash list

# Apply latest stash
git stash apply

# Apply and remove stash
git stash pop

# Apply specific stash
git stash apply stash@{1}

# Show stash details
git stash show -p

# Delete specific stash
git stash drop stash@{0}

# Delete all stashes
git stash clear

# Include untracked files
git stash -u
```

---

# Git Stash vs Git Commit

| Feature              | Git Stash | Git Commit |
| -------------------- | --------- | ---------- |
| Temporary Save       | ✅ Yes     | ❌ No       |
| Visible in History   | ❌ No      | ✅ Yes      |
| Creates Commit       | ❌ No      | ✅ Yes      |
| Quick Context Switch | ✅ Yes     | ❌ No       |

---

# Best Use Cases

* Branch switch karna ho
* Urgent bug fix karna ho
* Pull karne se pehle changes save karna ho
* Half-completed work temporarily save karna ho
* Experiment karna ho bina commit ke

---

