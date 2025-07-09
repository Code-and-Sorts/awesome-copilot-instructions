---
description: Systematic task execution workflow with proper testing and git practices for AI-assisted development
applyTo: "**/*.{js,ts,py,java,go,rs,rb,php,cs}"
---

# Task Execution and Management Workflow

## Overview

This workflow provides a systematic approach to executing development tasks generated from PRDs. It emphasizes controlled progress, proper testing, and clean git practices to ensure reliable AI-assisted development.

## Core Principles

### One Task at a Time

- **Execute one sub-task at a time** - Do not start the next sub-task until the current one is complete
- **Seek approval** - Ask for user permission before starting each new sub-task
- **Wait for confirmation** - User must respond "yes", "y", or equivalent before proceeding

### Progress Tracking

- **Update immediately** - Mark tasks as completed `[x]` as soon as they're finished
- **Maintain accuracy** - Keep the task list current and accurate
- **Document changes** - Update the "Relevant Files" section with every modification

## Task Execution Protocol

### Step 1: Task Selection

1. Identify the next available task (not blocked by dependencies)
2. Review task requirements and acceptance criteria
3. Confirm prerequisites are met
4. Ask user for permission to proceed

### Step 2: Implementation

1. **Plan the approach** - Outline implementation strategy
2. **Implement the feature** - Write code using GitHub Copilot
3. **Test locally** - Verify functionality works as expected
4. **Mark sub-task complete** - Update task list with `[x]`

### Step 3: Completion Protocol

When **all sub-tasks** under a parent task are marked `[x]`:

1. **Run full test suite**

   ```bash
   # Examples for different frameworks
   pytest                 # Python
   npm test              # Node.js
   bin/rails test        # Ruby on Rails
   cargo test            # Rust
   go test ./...         # Go
   ```

2. **Only if all tests pass** - Proceed to next steps
3. **Stage changes** - `git add .`
4. **Clean up** - Remove temporary files and code
5. **Commit with structured message** - Use conventional commit format

### Step 4: Git Commit Guidelines

Use single-line format with multiple `-m` flags:

```bash
git commit -m "feat: add payment validation logic" \
           -m "- Validates card type and expiry" \
           -m "- Adds unit tests for edge cases" \
           -m "Related to T123 in PRD"
```

#### Commit Message Structure

- **Type**: `feat`, `fix`, `refactor`, `test`, `docs`, `style`, `perf`
- **Summary**: Brief description of what was accomplished
- **Details**: Key changes and additions (use additional `-m` flags)
- **Reference**: Task number and PRD context

### Step 5: Parent Task Completion

1. Mark **parent task** as completed `[x]`
2. Update relevant files list
3. Ask user permission for next task

## Task List Management

### Status Updates

```markdown
- [x] **T001: Completed Task**
  - [x] Completed sub-task 1
  - [x] Completed sub-task 2
  
- [ ] **T002: In Progress Task**
  - [x] Completed sub-task 1
  - [ ] Current sub-task 2
  - [ ] Pending sub-task 3
```

### Relevant Files Section

Maintain an up-to-date list of all files created or modified:

```markdown
## Relevant Files
- `src/components/LoginForm.jsx` - User authentication form with validation
- `src/utils/validation.js` - Input validation helper functions
- `src/services/authService.js` - Authentication API calls
- `tests/auth.test.js` - Unit tests for authentication logic
```

## GitHub Copilot Integration

### Effective Prompting

1. **Context Setting**: Reference the current task and PRD section
2. **Specific Requests**: Ask for precise implementations
3. **Code Review**: Request validation against requirements
4. **Testing**: Generate appropriate test cases

### Example Prompts

```javascript
// Context setting
"Based on task T005 in the PRD, I need to implement user authentication..."

// Specific implementation
"Generate a login endpoint that validates email/password and returns JWT token"

// Code review
"Review this authentication middleware against the PRD security requirements"

// Testing
"Create unit tests for the login function covering success and error cases"
```

## Quality Assurance

### Before Marking Tasks Complete

- [ ] Functionality works as specified in PRD
- [ ] All edge cases are handled
- [ ] Error handling is implemented
- [ ] Code follows project conventions
- [ ] Tests are written and passing
- [ ] Documentation is updated

### Testing Strategy

1. **Unit Tests** - Test individual functions and components
2. **Integration Tests** - Test component interactions
3. **End-to-End Tests** - Test complete user workflows
4. **Manual Testing** - Verify UI/UX works as expected

## Common Execution Patterns

### Frontend Task Execution

1. Create component structure
2. Implement functionality
3. Add styling and responsive design
4. Handle user interactions and state
5. Add error handling
6. Write tests
7. Update documentation

### Backend Task Execution

1. Define API endpoints
2. Implement business logic
3. Add data validation
4. Handle errors and edge cases
5. Write unit tests
6. Test API endpoints
7. Update API documentation

### Database Task Execution

1. Design schema changes
2. Create migration scripts
3. Update models/entities
4. Test migrations
5. Verify data integrity
6. Update data access layer
7. Document schema changes

## Error Handling and Troubleshooting

### When Tests Fail

1. **Do not commit** - Fix issues before staging changes
2. **Debug systematically** - Isolate the problem
3. **Check dependencies** - Ensure all requirements are met
4. **Review PRD** - Verify implementation matches requirements
5. **Ask for help** - Request user guidance if stuck

### When Tasks Are Blocked

1. **Identify blocker** - Document what's preventing progress
2. **Communicate clearly** - Explain the issue to user
3. **Propose solutions** - Suggest alternatives or workarounds
4. **Update task list** - Mark dependencies that need resolution

## Best Practices

### Code Quality

- Follow existing code style and conventions
- Write self-documenting code with clear variable names
- Add appropriate error handling
- Include helpful code comments for complex logic
- Keep functions small and focused

### Git Practices

- Make atomic commits (one logical change per commit)
- Write clear, descriptive commit messages
- Test before committing
- Keep commit history clean and meaningful

### Documentation

- Update README files as needed
- Document API changes
- Add inline code documentation
- Keep architecture decisions recorded

### Communication

- Ask for clarification when requirements are unclear
- Provide regular progress updates
- Explain implementation decisions
- Request feedback on complex implementations

## Workflow Integration

This task execution workflow integrates with:

- **PRD Creation**: Reference PRD sections during implementation
- **Task Generation**: Follow task breakdown and dependencies
- **Code Review**: Validate implementations against PRD requirements
- **Testing**: Execute comprehensive testing strategy
- **Deployment**: Prepare code for production deployment
