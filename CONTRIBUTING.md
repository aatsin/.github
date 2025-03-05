# Git Branching and Commit Guidelines
This document outlines the process for creating branches and commits in our project. Our workflow is based on a single `main` branch, which serves as the central point of development. Task-specific branches will typically originate from `main`, with one branch per task and associated commits following a structured approach.

## Branching Strategy

### 1. Main Branch
- The `main` branch is the primary branch of the project and reflects the stable, production-ready codebase.
- No direct commits are allowed on `main`. All changes must come from task-specific branches via pull requests (PRs) or merge requests (MRs).
- `main` should always remain in a deployable state.

### 2. Task Branches
- For each task, feature, bug fix, or improvement, create a new branch off the `main` branch (unless specified otherwise or for some valid reason).
- Branch names should be descriptive and follow this convention:
  - Format: `<type>/<project-key>-<task-number>/<short-description>`
  - Types:
    - `feat` (for new features)
    - `bugfix` (for bug fixes)
    - `hotfix` (for urgent production fixes)
    - `refactor` (for code improvements without functional changes)
    - `docs` (for documentation updates)
  - Project Key: A short identifier for the project (e.g., `CBP`).
  - Task Number: The specific task identifier (e.g., `123`).
  - Examples:
    - `feat/CBP-123/add-user-authentication`
    - `bugfix/CBP-456/fix-login-error`
    - `refactor/CBP-789/cleanup-api-endpoints`
- Keep branches focused on a single task or purpose to maintain clarity and simplicity.

### 3. Creating a Branch
- Ensure your local repository is up-to-date with the latest changes from `main`:
```bash
  git checkout main
  git pull origin main
```
- Create and switch to your new branch:
```bash
  git checkout -b <branch-name>
``` 
Example:
```bash
  git checkout -b feat/CBP-123/add-user-authentication
```
## Commit Guidelines

### 1. Commit Structure
- Commits should be small, logical, and self-contained units of work.
- Each commit message must follow this format:
  - Format: `<type>(<scope>): <project-key>-<task-number> <short-description>`
  - Types:
    - `feat` (new feature)
    - `fix` (bug fix)
    - `refactor` (code refactoring)
    - `docs` (documentation changes)
    - `test` (adding or updating tests)
    - `chore` (miscellaneous tasks, e.g., updating dependencies)
  - Scope: A brief context (e.g., `auth`, `ui`, `api`).
  - Project Key: The project identifier (e.g., `CBP`).
  - Task Number: The specific task identifier (e.g., `123`).
  - Examples:
    - `feat(auth): CBP-123 add login endpoint`
    - `fix(ui): CF-456 correct button alignment on mobile`
    - `refactor(api): PRIGT-789 simplify error handling`

### 2. Writing Good Commits
Good commits follow best practices to ensure they’re clear, useful, and easy to track. Here are some guidelines:

**Descriptive and Concise Messages:**
- Write a message that explains what the change does and, if needed, why.
- Keep the first line short (under 50-72 characters) as a summary, and add more details in additional lines if necessary. Example:
```
  feat(auth): implement JWT token validation (CBP-123)
  Added middleware to validate JWT tokens on protected routes.
  Updated unit tests to cover token expiration cases.
```

**Atomicity:**
- Each commit should represent a single, logical, complete change. Avoid mixing unrelated changes (e.g., bug fixes and new features in the same commit).

**Use the Right Verb Tense:**
- Write messages in the present imperative tense (e.g., "Add login function" instead of "Added login function"). This is a common convention in tools like Git.
  
**Avoid Unnecessary Changes:**
- Don’t include auto-generated files or irrelevant changes (like whitespace edits without purpose).
- If more detail is needed, add a blank line after the first line and provide additional context:

- Commit early and often, but ensure each commit is functional (e.g., does not break the build).

### 3. Committing Changes
- Stage and commit your changes:
```bash
  git add <files>
  git commit -m "feat(auth): CBP-123 add login endpoint"
```
- Push your branch to the remote repository:
```bash
  git push origin <branch-name>
```
## Workflow Example
1. Start a Task:
   - Update `main`:
```bash 
  git checkout main && git pull origin main
```
   - Create a branch:
```bash
  git checkout -b feat/CBP-123/add-user-authentication
```

2. Work on the Task:
   - Make changes and commit:
```bash
     git add .
     git commit -m "feat(auth): CBP-123 add login form validation"
```
   
   - Add more commits as needed:
```bash
     git add .
     git commit -m "test(auth): CBP-123 add unit tests for login form"
```
   
3. Push the Branch:
```bash
   git push origin feat/CBP-123/add-user-authentication
```
4. Create a Pull Request:
   - Open a PR from `feat/CBP-123/add-user-authentication` to `main`.
   - Include a description of the changes and reference the task (`CBP-123`).
   - Fill the template with the required fields.
5. Merge into Main:
   - After review and approval, `merge` the PR into `main` (preferably using a "Squash and Merge" or "Rebase and Merge" strategy to keep history clean).
   - Delete the task branch after merging.

## Additional Notes
- Rebasing: If your branch falls behind main, rebase it to keep history linear:
```bash
  git checkout feat/CBP-123/add-user-authentication
  git rebase main
```
  Resolve conflicts if necessary, then push:
```bash
  git push origin feat/CBP-123/add-user-authentication
```
- Code Reviews: All PRs must be reviewed and approved by at least one team member before merging.
- Keep Branches Short-Lived: Aim to complete and merge task branches quickly to avoid long-running branches.
By following these guidelines , we ensure a clean, organized, and collaborative development process. If you have questions or need clarification, reach out to the team!
