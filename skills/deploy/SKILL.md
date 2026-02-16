---
name: deploy
description: deploy a product with git and GitHub
---

# Deploy

## Step-by-step

### 1. Commit

- ONLY staged files
- Think and write the commit message following Conventional Commits

#### Commands

- git commit

--------------------------------

### 2. Push

#### Commands

- git push

--------------------------------

### 3. Create a PR

#### Commands

- gh pr create

--------------------------------

### 4. Review

- Wait until the action on GitHub is green

--------------------------------

### 5. Review by a human

- Wait until the PR is merged

--------------------------------

### 6. Deploy

- Wait until the action on GitHub is green

--------------------------------

### 7. Clean up

- git checkout main
- git pull
- remove unnecessary branches
