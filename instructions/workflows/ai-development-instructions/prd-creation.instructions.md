---
description: Workflow for creating comprehensive Product Requirements Documents (PRDs) for AI-assisted development
applyTo: "**/*.md"
---

# Product Requirements Document (PRD) Creation Workflow

## Overview

This workflow guides you through creating comprehensive Product Requirements Documents (PRDs) that serve as the foundation for AI-assisted development tasks. The PRD should be detailed enough for a junior developer to understand and implement.

## Process

### Step 1: Initial Assessment

When a user provides a feature request or project idea, first ask clarifying questions to understand:

- **Problem/Goal**: What specific problem are we solving?
- **Target User**: Who will use this feature?
- **Core Functionality**: What are the main capabilities needed?
- **User Stories**: How will users interact with this feature?
- **Acceptance Criteria**: What defines "done"?
- **Scope/Boundaries**: What's included and excluded?
- **Data Requirements**: What data needs to be stored/processed?
- **Design/UI**: Any specific design requirements?
- **Edge Cases**: What unusual scenarios should we handle?

### Step 2: PRD Structure

Create a comprehensive PRD with these sections:

#### 1. Introduction/Overview

- Brief description of the feature
- Context and background
- Problem statement

#### 2. Goals

- Primary objectives
- Business value
- User value

#### 3. User Stories

- As a [user type], I want [functionality] so that [benefit]
- Include multiple user personas if applicable

#### 4. Functional Requirements

- Detailed feature specifications
- User interactions and flows
- Data requirements
- Integration points

#### 5. Non-Goals

- Explicitly state what's out of scope
- Future considerations

#### 6. Design Considerations

- UI/UX requirements
- Accessibility considerations
- Mobile/responsive requirements

#### 7. Technical Considerations

- Performance requirements
- Security considerations
- Scalability needs
- Integration requirements

#### 8. Success Metrics

- How will we measure success?
- Key performance indicators
- Acceptance criteria

#### 9. Open Questions

- Unresolved issues
- Items requiring further clarification

### Step 3: File Management

- Save the PRD as `prd-[feature-name].md` in a `/tasks` directory
- Use clear, descriptive filename
- Ensure proper markdown formatting

## Writing Guidelines

### Clarity and Precision

- Write for a junior developer audience
- Be explicit and unambiguous
- Avoid jargon and technical assumptions
- Use concrete examples where possible

### Structure and Format

- Use consistent markdown formatting
- Include clear headings and subheadings
- Use bullet points for lists
- Include code examples where relevant

### Completeness

- Address all aspects of the feature
- Include error handling scenarios
- Consider edge cases and boundary conditions
- Specify data validation requirements

## Example PRD Template

```markdown
# PRD: [Feature Name]

## Introduction
Brief description of what we're building and why.

## Goals
- Primary goal
- Secondary goals
- Business objectives

## User Stories
- As a [user type], I want [action] so that [benefit]
- As a [user type], I want [action] so that [benefit]

## Functional Requirements
### Core Features
- Feature 1: Description
- Feature 2: Description

### User Interactions
- Step-by-step user flows
- Input validation requirements
- Error handling

## Non-Goals
- What we're NOT building
- Future considerations

## Design Considerations
- UI/UX requirements
- Accessibility needs
- Mobile responsiveness

## Technical Considerations
- Performance requirements
- Security considerations
- Integration points

## Success Metrics
- How we'll measure success
- Acceptance criteria

## Open Questions
- Unresolved issues
- Items needing clarification
```

## Best Practices

### For GitHub Copilot Users

- Use this PRD as context when starting development
- Reference specific sections when asking Copilot for implementation help
- Keep the PRD updated as requirements evolve
- Use PRD sections as prompts for generating code

### Quality Assurance

- Review PRD with stakeholders before starting development
- Ensure all requirements are testable
- Validate that success metrics are measurable
- Confirm technical feasibility

### Documentation

- Keep PRDs version controlled
- Link to related documents and resources
- Update PRDs as requirements change
- Archive completed PRDs for reference

## Integration with Development Workflow

This PRD creation process integrates with:

- **Task Generation**: Use the completed PRD to generate specific development tasks
- **Task Execution**: Reference PRD sections during implementation
- **Code Review**: Validate implementations against PRD requirements
- **Testing**: Create test cases based on PRD specifications
