# Kubernetes Operations

Comprehensive Kubernetes cluster management for your agents.

## Features

- **Read Operations**: Get resources, list resources, watch for changes
- **Write Operations**: Create, update, patch, delete resources
- **Monitoring**: Stream logs, watch events
- **Management**: Scale deployments, restart pods

## Node Types

| Node Type | Description |
|-----------|-------------|
| `k8s-get` | Get a specific Kubernetes resource |
| `k8s-list` | List resources by type/namespace |
| `k8s-logs` | Stream pod logs |
| `k8s-events` | Watch cluster events |
| `k8s-restart` | Restart deployments/pods |
| `k8s-scale` | Scale deployments up/down |
| `k8s-patch` | Patch resource configurations |
| `k8s-delete` | Delete Kubernetes resources |
| `k8s-watch` | Watch for resource changes |

## Configuration

Requires Kubernetes cluster access configured in your Axiom deployment.

## License

MIT