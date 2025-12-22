---
title: Commit Message Generator
description: Generate clear, conventional commit messages following best practices.
tags:
  - Git
  - Commit
  - Conventional Commits
  - Workflow
author: VibeBaza
featured: true
---

Generate a commit message for the following changes.

## Format

Use conventional commits format:

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

## Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Formatting, missing semicolons, etc.
- `refactor`: Code restructuring without behavior change
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks, dependencies

## Guidelines

1. **Subject line**: 50 characters max, imperative mood
2. **Body**: Explain what and why, not how
3. **Footer**: Reference issues, breaking changes

## Examples

```
feat(auth): add OAuth2 login with Google

Implement Google OAuth2 authentication flow.
Users can now sign in using their Google accounts.

Closes #123
```

```
fix(api): handle null response from external service

The external API occasionally returns null instead of
an empty array. Added null check to prevent crashes.

Fixes #456
```

```
refactor(database): extract query builder into service

Move complex query construction logic from controllers
to a dedicated QueryBuilder service for better testability.
```

---

Now analyze the diff and generate an appropriate commit message.
