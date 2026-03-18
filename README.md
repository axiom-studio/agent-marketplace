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
├── CONTRIBUTING.md           # Contribution guidelines
└── agents/                   # Agent definitions
    ├── text-summarizer/
    │   ├── agent.yaml        # Agent definition (nodes, connections, schemas)
    │   └── README.md         # Agent documentation
    ├── email-sender/
    ├── json-transformer/
    └── webhook-receiver/
```

## Agent Definition Format

Each agent is defined in a single `agent.yaml` file:

```yaml
apiVersion: axiom.studio/v1
kind: AgentLibraryVersion
metadata:
  name: Agent Name
  description: What the agent does
  version: 1.0.0
  category: ml-inference
  tags:
    - tag1
    - tag2
  author: Your Name
  authorEmail: your@email.com
  license: Apache-2.0

spec:
  nodes:
    - id: input
      type: input
      position: { x: 100, y: 200 }
      config: { ... }
    - id: process
      type: llm-inference
      position: { x: 400, y: 200 }
      config: { ... }
    - id: output
      type: output
      position: { x: 700, y: 200 }
      config: { ... }

  connections:
    - sourceNodeId: input
      targetNodeId: process
    - sourceNodeId: process
      targetNodeId: output

  inputSchema:
    field1:
      type: string
      required: true

  outputSchema:
    result:
      type: string

  dependencies:
    nodeTypes:
      - llm-inference
    permissions:
      - network:outbound
```

## Creating Your Own Marketplace

1. Fork this repository
2. Modify `marketplace.yaml` with your details
3. Add your agents in the `agents/` directory
4. Each agent needs:
   - `agent.yaml` - Required. Agent definition with nodes, connections, and schemas
   - `README.md` - Recommended. Documentation

5. Add the repository URL to Axiom Studio

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

## License

This repository is licensed under the Apache License 2.0. See [LICENSE](LICENSE) for details.

## Support

- 📖 [Documentation](https://docs.axiomstudio.ai/agents/marketplace)
- 💬 [Discord](https://discord.gg/axiomstudio)
- 🐛 [Issue Tracker](https://github.com/axiomstudio/agent-marketplace/issues)