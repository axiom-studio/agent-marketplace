# Axiom Agent Marketplace

Official marketplace repository for Axiom Studio agent workflows. This repository contains pre-built, production-ready agents that can be discovered and imported directly into Axiom Studio.

## Overview

This marketplace follows the [Axiom Marketplace Specification](https://docs.axiomstudio.ai/marketplace/spec) and serves as a reference implementation for creating your own marketplace repositories.

## Available Agents

### Data Processing

| Agent | Description | Version |
|-------|-------------|---------|
| [JSON Transformer](agents/json-transformer) | Transform JSON data using templates and mappings | 1.0.0 |

### ML & AI

| Agent | Description | Version |
|-------|-------------|---------|
| [Text Summarizer](agents/text-summarizer) | Summarize long text into concise summaries using AI | 1.0.0 |

### Notifications

| Agent | Description | Version |
|-------|-------------|---------|
| [Email Sender](agents/email-sender) | Send emails with templates and attachments | 1.0.0 |

### Integration

| Agent | Description | Version |
|-------|-------------|---------|
| [Webhook Receiver](agents/webhook-receiver) | Receive and process webhook events from external services | 1.0.0 |

## Adding to Axiom Studio

1. Navigate to **Agents → Marketplace** in Axiom Studio
2. Click **Add agent source**
3. Enter the repository URL: `https://github.com/axiomstudio/agent-marketplace`
4. Click **Save** - the repository will be synced automatically

## Repository Structure

```
agent-marketplace/
├── marketplace.yaml          # Repository metadata
├── README.md                 # This file
├── LICENSE                   # Apache 2.0 License
└── agents/                   # Agent definitions
    ├── text-summarizer/
    │   ├── agent.yaml        # Agent metadata
    │   ├── workflow.yaml     # Workflow definition
    │   ├── input-schema.yaml # Input schema
    │   ├── output-schema.yaml# Output schema
    │   └── README.md         # Agent documentation
    ├── email-sender/
    ├── json-transformer/
    └── webhook-receiver/
```

## Creating Your Own Marketplace

1. Fork this repository
2. Modify `marketplace.yaml` with your details
3. Add your agents in the `agents/` directory
4. Each agent needs:
   - `agent.yaml` - Required. Agent metadata and configuration
   - `workflow.yaml` - Required. Workflow definition
   - `input-schema.yaml` - Optional. Input validation schema
   - `output-schema.yaml` - Optional. Output schema
   - `README.md` - Recommended. Documentation

5. Add the repository URL to Axiom Studio

## Agent Specification

Each agent must have an `agent.yaml` file following this structure:

```yaml
apiVersion: marketplace.axiomstudio.ai/v1
kind: AgentListing
metadata:
  id: unique-agent-id
  name: Agent Display Name
  description: Brief description of what the agent does
  version: 1.0.0
  category: category-name
  tags:
    - tag1
    - tag2
  author: Your Name
  authorEmail: your@email.com
  license: Apache-2.0

spec:
  skills: []           # Required skills
  nodeTypes: []        # Required node types
  permissions: []      # Required permissions
  inputSchema: ./input-schema.yaml
  outputSchema: ./output-schema.yaml
  workflow: ./workflow.yaml
  defaultConfig: {}    # Default configuration
  env: []              # Environment variables
```

## Categories

Standard categories used in this marketplace:

- `data-processing` - Data transformation, ETL, processing
- `ml-inference` - Machine learning and AI inference
- `notifications` - Alerts, messaging, notifications
- `integration` - Third-party service integrations
- `automation` - Workflow automation
- `utilities` - Helper and utility agents

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Adding a New Agent

1. Create a new directory under `agents/` with your agent ID
2. Add all required files (`agent.yaml`, `workflow.yaml`)
3. Add documentation (`README.md`)
4. Test your agent locally
5. Submit a pull request

## License

This repository is licensed under the Apache License 2.0. See [LICENSE](LICENSE) for details.

Individual agents may have their own licenses specified in their `agent.yaml` file.

## Support

- 📖 [Documentation](https://docs.axiomstudio.ai/agents/marketplace)
- 💬 [Discord](https://discord.gg/axiomstudio)
- 🐛 [Issue Tracker](https://github.com/axiomstudio/agent-marketplace/issues)