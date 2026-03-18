# Contributing to Axiom Agent Marketplace

Thank you for your interest in contributing to the Axiom Agent Marketplace! This document provides guidelines and instructions for contributing.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Contributing Process](#contributing-process)
- [Agent Guidelines](#agent-guidelines)
- [Testing](#testing)
- [Documentation](#documentation)
- [Pull Request Process](#pull-request-process)

## Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/0/code_of_conduct/). By participating, you are expected to uphold this code.

## Getting Started

1. Fork the repository
2. Clone your fork locally
3. Create a new branch for your contribution
4. Make your changes
5. Submit a pull request

## Development Setup

### Prerequisites

- Git
- Axiom Studio (for testing agents)
- YAML validator (optional, recommended)

### Clone and Setup

```bash
git clone https://github.com/YOUR_USERNAME/agent-marketplace.git
cd agent-marketplace
```

## Contributing Process

### Adding a New Agent

1. Create a new directory under `agents/` with your agent's ID (lowercase, hyphens only):
   ```bash
   mkdir agents/my-new-agent
   ```

2. Create the required files:
   ```bash
   touch agents/my-new-agent/agent.yaml
   touch agents/my-new-agent/workflow.yaml
   touch agents/my-new-agent/README.md
   ```

3. Optionally add schemas:
   ```bash
   touch agents/my-new-agent/input-schema.yaml
   touch agents/my-new-agent/output-schema.yaml
   ```

4. Implement your agent following the [Agent Guidelines](#agent-guidelines)

### Modifying an Existing Agent

1. Locate the agent in `agents/`
2. Make your changes
3. Update the version in `agent.yaml` following [Semantic Versioning](https://semver.org/)
4. Update the README if needed

## Agent Guidelines

### Naming Conventions

- **Agent ID**: lowercase with hyphens (e.g., `text-summarizer`)
- **Agent Name**: Title Case with spaces (e.g., `Text Summarizer`)
- **Files**: Use lowercase with hyphens or underscores

### Required Files

#### agent.yaml

```yaml
apiVersion: marketplace.axiomstudio.ai/v1
kind: AgentListing
metadata:
  id: your-agent-id          # Required: unique identifier
  name: Your Agent Name       # Required: display name
  description: Short description  # Required: brief description
  version: 1.0.0              # Required: semantic version
  category: category-name     # Required: see categories below
  tags:                       # Required: at least one tag
    - tag1
    - tag2
  author: Your Name           # Required
  authorEmail: your@email.com # Required
  license: Apache-2.0         # Required

spec:
  skills: []                  # List of required skills
  nodeTypes: []               # List of required node types
  permissions: []             # List of required permissions
  inputSchema: ./input-schema.yaml   # Optional
  outputSchema: ./output-schema.yaml # Optional
  workflow: ./workflow.yaml   # Required
  defaultConfig: {}           # Default configuration values
  env: []                     # Environment variables needed
```

#### workflow.yaml

Define the agent's workflow using the Axiom workflow specification:

```yaml
apiVersion: workflow.axiomstudio.ai/v1
kind: Workflow
metadata:
  name: your-agent-id
spec:
  entryPoint: main
  nodes:
    - id: input
      type: input
      # ...
    - id: main
      type: process
      # ...
    - id: output
      type: output
      # ...
```

#### README.md

Each agent should have a README with:

- Overview and description
- Requirements (skills, environment variables)
- Input/Output specification
- Usage examples
- Configuration options
- Changelog

### Categories

Use one of the standard categories:

| Category | Description |
|----------|-------------|
| `data-processing` | Data transformation, ETL, processing |
| `ml-inference` | Machine learning and AI inference |
| `notifications` | Alerts, messaging, notifications |
| `integration` | Third-party service integrations |
| `automation` | Workflow automation |
| `utilities` | Helper and utility agents |

### Versioning

Follow [Semantic Versioning](https://semver.org/):

- **MAJOR**: Breaking changes to input/output schema
- **MINOR**: New features, backward compatible
- **PATCH**: Bug fixes, backward compatible

## Testing

### Local Testing

1. Add your local marketplace to Axiom Studio:
   - Use a file:// URL or local git server
   - Or push to a test branch on your fork

2. Import and test your agent

3. Verify:
   - Input validation works correctly
   - Workflow executes as expected
   - Output matches the schema
   - Error handling is appropriate

### Validation Checklist

- [ ] `agent.yaml` is valid YAML
- [ ] `workflow.yaml` is valid YAML
- [ ] All required fields are present
- [ ] Agent ID is unique
- [ ] Version follows semver
- [ ] Category is valid
- [ ] README is complete
- [ ] Tested in Axiom Studio

## Documentation

### README Structure

```markdown
# Agent Name

Brief description of what the agent does.

## Overview

Detailed explanation of the agent's purpose and use cases.

## Requirements

### Skills
- List required skills

### Environment Variables
- List required env vars

## Usage

### Input

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| ... | ... | ... | ... |

### Output

| Field | Type | Description |
|-------|------|-------------|
| ... | ... | ... |

### Example

Input and output example.

## Configuration

Configuration options table.

## Changelog

### vX.Y.Z
- Changes
```

## Pull Request Process

1. **Create a Branch**
   ```bash
   git checkout -b feature/my-new-agent
   ```

2. **Make Your Changes**
   - Follow the agent guidelines
   - Test thoroughly
   - Update documentation

3. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "feat: add my-new-agent"
   ```

   Use conventional commits:
   - `feat:` for new agents
   - `fix:` for bug fixes
   - `docs:` for documentation
   - `chore:` for maintenance

4. **Push and Create PR**
   ```bash
   git push origin feature/my-new-agent
   ```

5. **PR Requirements**
   - Clear description of changes
   - Link to any related issues
   - All CI checks passing
   - At least one approval from maintainers

### PR Review Criteria

- Code quality and style
- Documentation completeness
- Test coverage
- Backward compatibility
- Security considerations

## Getting Help

- 📖 [Documentation](https://docs.axiomstudio.ai/agents/marketplace)
- 💬 [Discord](https://discord.gg/axiomstudio)
- 🐛 [Issue Tracker](https://github.com/axiomstudio/agent-marketplace/issues)

Thank you for contributing! 🎉