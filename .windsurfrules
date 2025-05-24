# 🚀 Project Development Rules & Standards

## 📋 Table of Contents
- [1. Development Workflow](#1-development-workflow)
- [2. Branching Strategy](#2-branching-strategy)
- [3. Commit Guidelines](#3-commit-guidelines)
- [4. Code Style](#4-code-style)
- [5. Testing Standards](#5-testing-standards)
- [6. Pull Request Process](#6-pull-request-process)
- [7. Documentation](#7-documentation)
- [8. Security Guidelines](#8-security-guidelines)

## 1. Development Workflow

### 1.1 Task Management
- All work is tracked in the project backlog
- Tasks are classified as: Feature, Bug, or Chore
- Use Fibonacci sequence (0, 1, 2, 3, 5, 8) for story point estimation

### 1.2 Development Flow
1. **Start** the top unstarted story from the backlog
2. **Branch** from `main` using naming convention: `{type}/{id}-description`
   - `feature/123-add-user-auth`
   - `bug/456-fix-login-error`
   - `chore/789-update-deps`
3. **Develop** using TDD approach:
   - Write failing tests (Red)
   - Implement minimal code to pass (Green)
   - Refactor (Refactor)
4. **Commit** frequently with descriptive messages
5. **Push** to remote and create PR when ready for review
6. **Review** and address feedback
7. **Merge** when approved and all checks pass
8. **Deploy** through CI/CD pipeline

## 2. Branching Strategy

### 2.1 Branch Types
- `main` - Production-ready code
- `staging` - Pre-production testing
- `feature/*` - New features
- `bug/*` - Bug fixes
- `chore/*` - Maintenance tasks

### 2.2 Branch Naming
```
{type}/{ticket-id}-{description}
```
Example: `feature/123-add-user-authentication`

## 3. Commit Guidelines

### 3.1 Commit Message Format
```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

### 3.2 Commit Types
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation changes
- `style`: Formatting, missing semi-colons, etc. (no code change)
- `refactor`: Code change that neither fixes a bug nor adds a feature
- `perf`: Code change that improves performance
- `test`: Adding missing tests or correcting existing tests
- `chore`: Changes to the build process or auxiliary tools

### 3.3 Examples
```
feat(auth): add Google OAuth login
fix(api): resolve 500 error on user creation
docs: update API documentation
```

## 4. Code Style

### 4.1 General
- Use 2 spaces for indentation
- Maximum line length: 100 characters
- Use single quotes for strings
- Always use semicolons
- Trailing commas in multi-line objects/arrays
- Use ES6+ features where applicable

### 4.2 Naming Conventions
- Variables/Functions: `camelCase`
- Classes/Constructors: `PascalCase`
- Constants: `UPPER_SNAKE_CASE`
- Private members: `_privateMethod`
- Files: `kebab-case.js`

### 4.3 File Structure
```
src/
  components/    # Reusable UI components
  pages/         # Page components
  hooks/         # Custom React hooks
  utils/         # Utility functions
  services/      # API services
  store/         # State management
  styles/        # Global styles
  types/         # TypeScript type definitions
  tests/         # Test files
  __mocks__/     # Test mocks
```

## 5. Testing Standards

### 5.1 Test Structure
- Unit tests: `*.test.js` or `*.spec.js`
- Test files live next to the code they test
- Use `describe` and `it` blocks
- Follow AAA pattern: Arrange, Act, Assert

### 5.2 Coverage Requirements
- Minimum 80% test coverage
- 100% coverage for critical paths
- Test both success and error cases

### 5.3 Testing Tools
- Jest for unit testing
- React Testing Library for components
- Cypress for E2E testing
- MSW for API mocking

## 6. Pull Request Process

### 6.1 PR Guidelines
- Link to related issue/ticket
- Provide clear description of changes
- Include screenshots for UI changes
- Ensure all tests pass
- Update documentation if needed
- Get at least one approval before merging

### 6.2 PR Template
```markdown
## Description
[Brief description of changes]

## Related Issues
- Fixes #123
- Related to #456

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Checklist
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Code review feedback addressed
```

## 7. Documentation

### 7.1 Project Documentation
- Keep `README.md` up to date
- Document architecture decisions (ADRs)
- Maintain API documentation
- Document environment variables

### 7.2 Code Documentation
- Use JSDoc for functions and components
- Document complex logic
- Keep comments up to date

## 8. Security Guidelines

### 8.1 General
- Never commit secrets or credentials
- Use environment variables for configuration
- Validate all user inputs
- Implement proper error handling
- Keep dependencies updated

### 8.2 Authentication/Authorization
- Use HTTPS in production
- Implement proper session management
- Use secure, httpOnly cookies for tokens
- Implement rate limiting
- Use CSRF protection

### 8.3 Data Protection
- Encrypt sensitive data
- Implement proper access controls
- Log security-relevant events
- Regular security audits

## 9. Performance Guidelines

### 9.1 Frontend
- Code splitting
- Lazy loading
- Optimize images
- Minimize re-renders
- Use memoization where appropriate

### 9.2 Backend
- Implement caching
- Optimize database queries
- Use pagination for large datasets
- Implement rate limiting

## 10. Dependencies

### 10.1 Management
- Use exact versions in package.json
- Audit dependencies regularly
- Document major version upgrades
- Keep dependencies up to date

### 10.2 Security
- Run `npm audit` regularly
- Address critical vulnerabilities immediately
- Use Dependabot for security updates

## 11. CI/CD

### 11.1 Pipeline
- Run tests on every push
- Build and test on PR
- Deploy to staging on merge to main
- Manual approval for production deploys

### 11.2 Environments
- Development
- Staging
- Production

## 12. Monitoring and Logging

### 12.1 Monitoring
- Set up error tracking
- Monitor performance metrics
- Set up alerts for critical issues

### 12.2 Logging
- Use structured logging
- Include request IDs
- Log appropriate levels (error, warn, info, debug)
- Don't log sensitive information

## 13. Code Review Guidelines

### 13.1 Review Process
- Review code for functionality and style
- Check for security issues
- Ensure tests are adequate
- Verify documentation is updated
- Be constructive and respectful

### 13.2 What to Look For
- Code quality and readability
- Performance implications
- Security vulnerabilities
- Test coverage
- Documentation

## 14. On-call and Incident Response

### 14.1 Incident Response
- Document incidents and resolutions
- Conduct post-mortems for major incidents
- Update runbooks based on learnings

### 14.2 On-call
- Rotate on-call responsibilities
- Document on-call procedures
- Set up proper alerting thresholds

## 15. Continuous Improvement

### 15.1 Retrospectives
- Hold regular retrospectives
- Document action items
- Follow up on improvements

### 15.2 Learning
- Share knowledge within the team
- Document lessons learned
- Stay updated with best practices

---

*Last Updated: May 25, 2025*
