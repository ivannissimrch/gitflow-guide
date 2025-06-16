# Chingu Team Git Workflow Guide

This guide explains how to set up and use our Git workflow to collaborate effectively and avoid merge conflicts during our project.

---

## One-Time Setup (only one person does this)

### 1. Create and set up the `dev` branch

```bash
git checkout -b dev
git push origin dev
```

### 2. Make `dev` the default branch

- Go to GitHub → Settings → Branches
- Change default branch from `main` to `dev`

### 3. Protect your branches

Go to GitHub → Settings → Branches → Add rule

**For both `main` and `dev` branches:**

- ✅ Require a pull request before merging
- ✅ Require at least one approving review

### 4. Add a Pull Request Template.

there is a pull request folder on this repo that you can copy and use as your template

1. Create `.github/pull_request_template.md` in your repo
2. Add your team's PR template content
3. Push to `dev` branch

---

## How Our Branches Work

| Branch      | Purpose                              | Who uses it      |
| ----------- | ------------------------------------ | ---------------- |
| `main`      | Production code - **don't touch!**   | Releases only    |
| `dev`       | Where everyone's work comes together | All team members |
| `feature/*` | Your individual work                 | You              |

**Examples:** `feature/login-page`, `feature/api-setup`, `fix/navbar-bug`

---

## Daily Workflow

### Starting a new task

1. **Get the latest code**

   ```bash
   git checkout dev
   git pull origin dev
   ```

2. **Create your feature branch**

   ```bash
   git checkout -b feature/your-task-name
   ```

3. **Work and commit**
   ```bash
   # Do your coding work
   git add .
   git commit -m "Add: short description of your work"
   git push origin feature/your-task-name
   ```

### Before submitting your work

**Important: Always do this to avoid conflicts!**

1. **Get the latest changes**

   ```bash
   git checkout dev
   git pull origin dev
   ```

2. **Update your branch**

   ```bash
   git checkout feature/your-task-name
   git merge dev
   ```

3. **Fix any conflicts and test your code**

### Submitting your work

1. **Create a Pull Request on GitHub**

   - From: your `feature/your-task-name` branch
   - To: `dev` branch

2. **Fill out the PR template**

3. **Request a review** (use the Reviewers section)

4. **Notify the team in Discord**
   - Use `@voyager` and include your PR link

### After your PR is merged

**Clean up and get ready for the next task:**

```bash
git checkout dev
git pull origin dev
git branch -d feature/your-task-name  # Delete the old branch
git checkout -b feature/your-next-task
```

---

## Quick Reference Commands

```bash
# Start new work
git checkout dev && git pull origin dev
git checkout -b feature/task-name

# Before creating PR
git checkout dev && git pull origin dev
git checkout feature/task-name && git merge dev

# After PR is merged
git checkout dev && git pull origin dev
git branch -d feature/old-task-name
```

---

## Golden Rules

✅ **Always** work on feature branches, never directly on `dev` or `main`

✅ **Always** merge latest `dev` into your branch before creating a PR

✅ Keep PRs small and focused on one task

✅ Review teammates' PRs when requested

✅ Test your code before submitting

❌ **Never** push directly to `main` or `dev`

❌ **Never** merge your own PRs without review

---

This workflow keeps our collaboration smooth, our code clean, and our project on track!
# gitflow-guide
