# Eerie Tea - Code Review Process

This document outlines the code review process for the Eerie Tea e-commerce project.

---

## Overview

Code reviews are mandatory for all changes to the main branch. This ensures code quality, knowledge sharing, and consistency across the project.

---

## Process Flow

### 1. Create a Branch

```bash
# Create feature branch from main
git checkout -b feature/product-search
# or
git checkout -b fix/cart-sync-issue
```

**Branch Naming Convention:**
- `feature/` - New features
- `fix/` - Bug fixes
- `refactor/` - Code refactoring
- `docs/` - Documentation updates
- `test/` - Test additions/updates
- `chore/` - Maintenance tasks

### 2. Make Changes

- Write code following [CODING_STANDARDS.md](./CODING_STANDARDS.md)
- Write/update tests as needed
- Update documentation if necessary
- Ensure code compiles/builds successfully

### 3. Commit Changes

Use conventional commit messages:

```
feat: add product search functionality

- Implement search API endpoint
- Add search UI component
- Add search debouncing
- Update API client with search functions

Closes #123
```

**Commit Message Format:**
```
<type>: <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation
- `style`: Formatting (no code change)
- `refactor`: Code refactoring
- `test`: Adding/updating tests
- `chore`: Maintenance tasks

### 4. Push and Create Pull Request

```bash
git push origin feature/product-search
```

Then create a Pull Request (PR) on GitHub with:
- Clear title describing the change
- Description explaining what and why
- Link to related issue/task
- Screenshots (for UI changes)
- Checklist of changes

### 5. PR Template

Use this template for PRs:

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Related Task/Issue
Closes #123

## Changes Made
- [ ] Backend changes
- [ ] Frontend changes
- [ ] Database changes
- [ ] Documentation updates

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests added/updated
- [ ] Manual testing completed
- [ ] All tests passing

## Checklist
- [ ] Code follows coding standards
- [ ] Self-review completed
- [ ] Comments/documentation updated
- [ ] No console.logs or debug code
- [ ] Error handling implemented
- [ ] Performance considered
- [ ] Security considered
```

### 6. Code Review

#### For Reviewers

**Review Checklist:**

1. **Functionality**
   - [ ] Does the code work as intended?
   - [ ] Are edge cases handled?
   - [ ] Is error handling appropriate?

2. **Code Quality**
   - [ ] Follows coding standards
   - [ ] Code is readable and maintainable
   - [ ] No code duplication
   - [ ] Proper naming conventions

3. **Testing**
   - [ ] Tests are included (if applicable)
   - [ ] Tests are meaningful and cover edge cases
   - [ ] All tests pass

4. **Security**
   - [ ] No sensitive data exposed
   - [ ] Input validation present
   - [ ] Authorization checks in place

5. **Performance**
   - [ ] No obvious performance issues
   - [ ] Database queries are efficient
   - [ ] No unnecessary re-renders (frontend)

6. **Documentation**
   - [ ] Code is self-documenting
   - [ ] Complex logic is commented
   - [ ] API changes documented

**Review Guidelines:**

- Be constructive and respectful
- Explain **why** you're requesting changes
- Approve when satisfied, don't nitpick
- Request changes for legitimate issues
- Ask questions if something is unclear

**Review Comments:**

```markdown
# ✅ Good Review Comments

"Consider extracting this logic into a separate method for reusability."

"This might fail if productId is null. Can we add a null check?"

"I noticed this query might cause N+1. Consider using Include() to eager load."

# ❌ Bad Review Comments

"Wrong"

"Fix this"

"Bad code"
```

#### For Authors

- **Respond to all comments** - Address or discuss each comment
- **Be open to feedback** - Code review is a learning opportunity
- **Make requested changes** - Update code based on feedback
- **Ask questions** - If feedback is unclear, ask for clarification
- **Update PR** - Push new commits to address feedback

### 7. Approval and Merge

**Requirements for Merge:**

- [ ] At least one approval (for small changes)
- [ ] At least two approvals (for significant changes)
- [ ] All CI checks passing
- [ ] No merge conflicts
- [ ] All review comments addressed

**Merge Strategy:**

- **Squash and Merge** (recommended for feature branches)
- **Rebase and Merge** (for clean history)
- **Merge Commit** (for release branches)

After merge:
- Delete the feature branch
- Update related tasks/issues
- Deploy to staging (if applicable)

---

## Review Priorities

### High Priority (Review ASAP)

- Security-related changes
- Database migrations
- API contract changes
- Authentication/authorization changes
- Payment processing changes

### Medium Priority (Review within 24 hours)

- New features
- Bug fixes
- Refactoring

### Low Priority (Review within 48 hours)

- Documentation updates
- Test additions
- Styling changes
- Minor bug fixes

---

## Review Best Practices

### For Reviewers

1. **Review promptly** - Don't let PRs sit for days
2. **Review thoroughly** - Check all aspects, not just syntax
3. **Be specific** - Point to exact lines and explain issues
4. **Suggest solutions** - Don't just point out problems
5. **Approve when ready** - Don't request unnecessary changes

### For Authors

1. **Keep PRs small** - Easier to review and less error-prone
2. **Self-review first** - Review your own code before requesting review
3. **Write clear descriptions** - Help reviewers understand context
4. **Respond promptly** - Address feedback quickly
5. **Learn from feedback** - Apply learnings to future code

---

## Automated Checks

Before manual review, PRs must pass:

### Backend (.NET)

- [ ] Code compiles without errors
- [ ] All unit tests pass
- [ ] All integration tests pass
- [ ] Code analysis passes (no warnings)
- [ ] No security vulnerabilities

### Frontend (Next.js)

- [ ] Code builds without errors
- [ ] TypeScript type checking passes
- [ ] ESLint passes (no errors)
- [ ] Biome formatting passes
- [ ] All tests pass
- [ ] No console errors

### Both

- [ ] No merge conflicts
- [ ] PR follows template
- [ ] Commit messages follow convention

---

## Escalation

If there's disagreement during review:

1. **Discuss in PR comments** - Have a conversation
2. **Request additional reviewers** - Get more opinions
3. **Schedule a meeting** - For complex issues
4. **Document decision** - Record the outcome

---

## Tools

- **GitHub Pull Requests** - For code review
- **GitHub Actions** - For automated checks
- **CodeQL** - For security scanning
- **Dependabot** - For dependency updates

---

## Resources

- [GitHub Pull Request Best Practices](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Code Review Guidelines](https://google.github.io/eng-practices/review/)

---

**Last Updated:** 2026-01-XX
