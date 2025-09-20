---
created: 2025-09-20T10:48:44Z
last_updated: 2025-09-20T10:48:44Z
version: 1.0
author: Claude Code PM System
---

# Project Structure

## Directory Organization

### Root Level Files

```
.
├── .claude/                    # Main system directory
│   ├── agents/                 # Specialized AI agents
│   ├── commands/               # Executable command definitions
│   ├── context/                # Project knowledge base
│   ├── epics/                  # Local workspace (add to .gitignore)
│   ├── prds/                   # Product requirements docs
│   ├── scripts/                # Helper scripts
│   └── rules/                  # System rules and patterns
├── install/                    # Installation scripts and docs
├── .gitignore                  # Git ignore patterns
├── AGENTS.md                   # Agent documentation
├── CLAUDE.md                   # Claude Code instructions
├── COMMANDS.md                 # Command reference
├── LICENSE                     # MIT license
├── README.md                   # Main project documentation
└── screenshot.webp             # System demonstration
```

### System Directories

#### `.claude/agents/`
Contains specialized sub-agents for different task types:
- `code-analyzer.md` - Bug hunting and code analysis
- `file-analyzer.md` - Verbose file summarization
- `parallel-worker.md` - Parallel execution coordination
- `statusline-setup.md` - Status line configuration
- `test-runner.md` - Test execution and analysis
- `output-style-setup.md` - Output style creation

#### `.claude/commands/`
Organized by category:
- `context/` - Context management commands
- `pm/` - Project management workflow commands
- `testing/` - Test configuration and execution commands

#### `.claude/context/`
Project knowledge base files:
- `progress.md` - Current status and next steps
- `project-structure.md` - Directory organization (this file)
- `tech-context.md` - Technologies and dependencies
- `system-patterns.md` - Architectural patterns
- `product-context.md` - Requirements and users
- `project-brief.md` - Scope and objectives
- `project-overview.md` - Feature summary
- `project-vision.md` - Long-term direction
- `project-style-guide.md` - Coding standards

#### `.claude/epics/`
Local workspace for epic management (should be in .gitignore):
```
epics/
└── [epic-name]/
    ├── epic.md          # Implementation plan
    ├── [#].md          # Individual task files
    └── updates/        # Work-in-progress updates
```

#### `.claude/prds/`
Product Requirements Documents:
- `feature-name.md` - Comprehensive PRDs created through brainstorming

#### `.claude/scripts/`
Helper scripts for system operations:
- `pm/init.sh` - System initialization script

### Installation Structure

```
install/
├── README.md            # Installation guide
├── from-repo/          # Install from repository
├── from-url/           # Install from URL
└── manual/             # Manual installation
```

## File Naming Conventions

### Context Files
- Use kebab-case for names: `project-brief.md`
- Descriptive and purpose-driven: `system-patterns.md`
- Group by category in subdirectories

### Epic Files
- Epic directory: `epics/feature-name/`
- Epic plan: `epic.md`
- Task files: Start as `001.md`, `002.md`, rename to `{issue-id}.md` after GitHub sync
- Updates: `updates/datetime.md`

### PRD Files
- Use feature name: `memory-system.md`
- Include version in content if needed

### Command Files
- Category-based organization: `commands/pm/`
- Command name matches file: `epic-sync.md`
- Use hyphens for multi-word commands

## Git Strategy

### Files to Track
- All `.md` documentation files
- Installation scripts
- Command definitions
- Agent specifications
- LICENSE and README

### Files to Ignore (add to .gitignore)
```
.claude/epics/
.claude/prds/
.claude/context/ (optional, depends on workflow)
```

### Worktree Pattern
Each epic gets its own Git worktree for isolated development:
- Main repository: `/project/`
- Epic workspace: `/project-epic-name/`
- Clean merge when complete

## Module Organization

### Command System
Commands are modular and self-contained:
- Each command is a markdown file
- Includes frontmatter with allowed tools
- Follows consistent structure: purpose, usage, steps

### Agent System
Agents are specialized but consistent:
- Single purpose per agent
- Clear input→processing→output pattern
- Return concise summaries (10-20% of input)

### Context System
Context files are comprehensive but focused:
- Cover all essential project knowledge
- Updated regularly to stay current
- Provide fast onboarding for agents

## Integration Points

### GitHub Integration
- Uses standard GitHub API
- Works with any GitHub repository
- No special repository configuration needed

### Claude Code Integration
- Uses native Claude Code capabilities
- No additional dependencies required
- Works with any Claude Code project

### Cross-Platform Support
- Unix/Linux/macOS: bash scripts
- Windows: PowerShell scripts
- Pure markdown for portability