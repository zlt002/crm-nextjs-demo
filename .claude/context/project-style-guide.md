---
created: 2025-09-20T10:48:44Z
last_updated: 2025-09-20T10:48:44Z
version: 1.0
author: Claude Code PM System
---

# Project Style Guide

## Documentation Standards

### Markdown Conventions
- **File Naming**: Use kebab-case for all files: `project-brief.md`, not `projectBrief.md`
- **Headers**: Use ATX-style headers (# Header 1, ## Header 2)
- **Line Length**: Keep lines under 80 characters for readability
- **Lists**: Use hyphens (-) for unordered lists
- **Code Blocks**: Specify language for syntax highlighting
- **Links**: Use descriptive link text

### Frontmatter Requirements
All context files MUST include frontmatter:
```yaml
---
created: 2025-09-20T10:48:44Z  # Use REAL datetime
last_updated: 2025-09-20T10:48:44Z  # Update on changes
version: 1.0
author: Claude Code PM System
---
```

### Documentation Structure
1. **Executive Summary**: Brief overview at the top
2. **Table of Contents**: For files longer than 500 words
3. **Section Headers**: Clear, descriptive headers
4. **Code Examples**: Include where helpful
5. **Cross-References**: Link to related documents

## Command Development

### Command File Structure
```markdown
# Command Name

Brief description of what the command does.

## Required Rules

**IMPORTANT:** Before executing this command, read and follow:
- `.claude/rules/specific-rule.md` - For specific guidance

## Preflight Checklist

Before proceeding, complete these validation steps.
Do not bother the user with preflight checks progress.

### 1. Validation Step
- Check: `command to run`
- Action: What to do based on result

## Instructions

### 1. First Step
Detailed step-by-step instructions...

### 2. Second Step
Continue with clear, actionable steps...

## Error Handling

**Common Issues:**
- **Error name:** "Clear error message with solution"
```

### Command Naming
- Use prefix pattern: `/category:action`
- Examples: `/pm:prd-new`, `/context:create`, `/testing:run`
- Be descriptive but concise
- Use consistent verbs: create, update, delete, start, stop, list

### Tool Authorization
Always specify allowed tools in frontmatter:
```yaml
---
allowed-tools: Read, Write, LS, Bash, Task
---
```

## Agent Development

### Agent Patterns
All agents follow consistent patterns:
1. **Single Purpose**: One clear job per agent
2. **Context Reduction**: Return 10-20% of processed information
3. **Concise Output**: Summaries, not raw data
4. **Error Handling**: Graceful failure with clear messages

### Agent Types
- **code-analyzer**: Hunt bugs across multiple files
- **file-analyzer**: Summarize verbose files
- **test-runner**: Execute tests cleanly
- **parallel-worker**: Coordinate multiple streams

### Agent Communication
- **No Direct Communication**: Use coordinator agents
- **Consistent Return Format**: Status + summary
- **Progress Indicators**: For long-running operations
- **Error Boundaries**: Isolate failures

## Code Style (for implementation files)

### Shell Scripts
- **Shebang**: Always include `#!/bin/bash`
- **Variables**: Use UPPER_CASE for constants
- **Functions**: Use snake_case for function names
- **Comments**: Explain why, not what
- **Error Handling**: Check exit codes, provide meaningful errors

### Markdown in Code
- **Fenced Blocks**: Use triple backticks with language
- **Inline Code**: Use backticks for commands and variables
- **Escaping**: Properly escape special characters
- **Consistency**: Follow project patterns

## Project Structure

### Directory Organization
```
.claude/
├── agents/           # Agent specifications
├── commands/         # Command definitions
│   ├── context/      # Context management
│   ├── pm/           # Project management
│   └── testing/      # Test execution
├── context/          # Project knowledge
├── epics/            # Local workspace
├── prds/             # Product requirements
├── rules/            # System rules
└── scripts/          # Utility scripts
```

### File Naming
- **Commands**: Match the command name exactly
- **Context Files**: Use descriptive names with hyphens
- **Agent Files**: Match agent type name
- **Rule Files**: Use clear, specific names

## Context Files

### Content Guidelines
- **Be Comprehensive but Concise**: Cover all essential information
- **Stay Current**: Update when project changes
- **Be Actionable**: Provide information that helps with work
- **Use Examples**: Include where helpful
- **Link Related**: Reference other context files

### File Types and Purpose
- **progress.md**: Current status and next steps
- **project-structure.md**: Directory organization
- **tech-context.md**: Technologies and dependencies
- **system-patterns.md**: Architectural patterns
- **product-context.md**: Requirements and users
- **project-brief.md**: Scope and objectives
- **project-overview.md**: Feature summary
- **project-vision.md**: Long-term direction
- **project-style-guide.md**: This file

## Writing Style

### Tone and Voice
- **Professional but Approachable**: Clear and direct
- **Action-Oriented**: Focus on what to do
- **Concise**: Get to the point quickly
- **Consistent**: Use same terminology throughout
- **Inclusive**: Use "you" and "we" appropriately

### Grammar and Mechanics
- **Active Voice**: "Run the command" not "The command should be run"
- **Present Tense**: For current state and actions
- **Future Tense**: For plans and vision
- **Second Person**: For instructions ("you should...")
- **Lists**: For parallel information

### Formatting
- **Bold for Emphasis**: Use sparingly for key points
- **Code Blocks**: For all commands and code
- **Blockquotes**: For quotes or important notes
- **Tables**: For structured comparisons
- **Horizontal Rules**: To separate major sections

## Error Messages

### Principles
- **Clear and Specific**: What exactly went wrong
- **Actionable**: How to fix it
- **Consistent**: Follow same format
- **Non-Blaming**: Focus on solution, not fault

### Format
```
❌ Error: [Specific error message]
💡 Solution: [Clear steps to resolve]
```

### Common Patterns
- **Missing Dependencies**: "Install X with command Y"
- **Permission Issues**: "Check permissions for path X"
- **Network Issues**: "Check connection and retry"
- **Configuration**: "Update setting in file X"

## Testing Guidelines

### Test Command Structure
- **Clear Description**: What the test does
- **Prerequisites**: What needs to be set up
- **Steps**: Exact commands to run
- **Expected Results**: What to look for
- **Cleanup**: How to reset

### Test Output
- **Verbose**: Include full output for debugging
- **Structured**: Organized for easy reading
- **Error Details**: Full stack traces when needed
- **Success Indicators**: Clear pass/fail markers

## Version Control

### Git Practices
- **Meaningful Commits**: Clear, descriptive messages
- **Small Changes**: Atomic, focused commits
- **Branch Strategy**: Use feature branches
- **Pull Requests**: For all changes
- **Issue References**: Link commits to issues

### .gitignore Patterns
```
.claude/epics/
.claude/prds/
.claude/context/.tmp/
*.log
.DS_Store
```

## Integration Patterns

### GitHub Integration
- **Issue References**: Always use #number format
- **Mention Syntax**: Use @username for mentions
- **Label Conventions**: Use consistent labels
- **Milestone Organization**: Group related issues

### Claude Code Integration
- **Tool Usage**: Use appropriate tools for tasks
- **Context Management**: Preserve context efficiently
- **Agent Selection**: Choose right agent for job
- **Command Structure**: Follow established patterns

## Accessibility

### Documentation
- **Alt Text**: For images and diagrams
- **Semantic Structure**: Proper header hierarchy
- **Color Contrast**: Ensure readability
- **Link Text**: Descriptive, not "click here"

### Commands
- **Clear Feedback**: Always indicate what's happening
- **Progress Indicators**: For long operations
- **Error Recovery**: Clear paths forward
- **Consistent Output**: Predictable format

## Security Considerations

### Data Handling
- **No Secrets**: Never store API keys or tokens
- **Sensitive Data**: Clear from logs and output
- **User Privacy**: Don't collect unnecessary data
- **File Permissions**: Respect system permissions

### Input Validation
- **Sanitize Input**: Always validate user input
- **Path Traversal**: Prevent directory escape
- **Command Injection**: Use safe execution methods
- **Rate Limiting**: Prevent abuse

## Performance Guidelines

### Efficiency
- **Minimize Dependencies**: Use built-in tools when possible
- **Lazy Loading**: Load only what's needed
- **Caching**: Cache expensive operations
- **Parallel Processing**: Use agents for concurrent work

### Resource Usage
- **Memory**: Be mindful of memory usage
- **Disk Space**: Clean up temporary files
- **Network**: Minimize network calls
- **CPU**: Optimize expensive operations

## Updates and Maintenance

### Keeping Current
- **Regular Updates**: Update documentation when code changes
- **Deprecation**: Mark old features clearly
- **Migration Paths**: Provide upgrade paths
- **Breaking Changes**: Communicate clearly

### Quality Assurance
- **Testing**: Test all changes thoroughly
- **Documentation**: Update docs with code
- **Examples**: Keep examples current
- **Backwards Compatibility**: Maintain when possible