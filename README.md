# agent-sandbox

Fork of [kubernetes-sigs/agent-sandbox](https://github.com/kubernetes-sigs/agent-sandbox).

A sandbox environment for developing and testing AI agents with Kubernetes integration.

## Overview

agent-sandbox provides a controlled execution environment for AI agents, enabling safe experimentation with tool use, code execution, and Kubernetes cluster interactions.

## Features

- Isolated sandbox environments for agent execution
- Kubernetes-native deployment and orchestration
- Support for multiple agent frameworks
- Built-in observability and logging
- Configurable resource limits and security policies

## Prerequisites

- Python 3.10+
- Go 1.21+
- Kubernetes cluster (v1.28+) or [kind](https://kind.sigs.k8s.io/) for local development
- `kubectl` configured with cluster access

## Installation

### From PyPI

```bash
pip install agent-sandbox
```

### From Source

```bash
git clone https://github.com/your-org/agent-sandbox.git
cd agent-sandbox
pip install -e .
```

## Quick Start

```python
from agent_sandbox import Sandbox

# Create a sandbox instance
sandbox = Sandbox()

# Run a simple agent task
result = sandbox.run(
    task="List all files in the current directory",
    timeout=30,
)

print(result.output)
```

## Development

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute to this project.

### Setting Up a Local Environment

```bash
# Install development dependencies
pip install -e ".[dev]"

# Run tests
pytest

# Run linting
ruff check .
mypy .
```

### Running with kind

```bash
# Create a local cluster
kind create cluster --name agent-sandbox

# Deploy the sandbox controller
kubectl apply -f deploy/
```

## Configuration

Configuration can be provided via environment variables or a `config.yaml` file:

```yaml
sandbox:
  namespace: agent-sandbox
  image: ghcr.io/your-org/agent-sandbox:latest
  resource_limits:
    cpu: "500m"
    memory: "512Mi"
  timeout: 300
```

## License

Apache License 2.0 — see [LICENSE](LICENSE) for details.
