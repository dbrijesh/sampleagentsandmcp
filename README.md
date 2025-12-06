# SampleApp - Agent-Orchestrated AWS Development

An agent-based development workspace using specialized AI agents for the complete AWS software development lifecycle.

## MCP Servers Configuration

This project uses the following Model Context Protocol (MCP) servers:

### AWS MCP Servers

- **aws-kb** - AWS Knowledge Base for architectural guidelines and compliance standards
- **aws-doc** - AWS Documentation for service documentation and best practices  
- **aws-diagram** - AWS Diagram tools for architecture visualization
- **aws-cloudformation** - AWS CloudFormation for IaC template generation
- **aws-cdk-cli** - AWS CDK CLI for deployment and synthesis operations
- **aws-cloudwatch** - AWS CloudWatch for monitoring metrics, logs, and alarms
- **aws-app-signals** - AWS Application Signals for application observability

### Security & Quality MCP Servers

- **security-scan** - Security scanner for OWASP Top 10 vulnerability detection

## Setup Instructions

### 1. Install MCP Servers

The MCP servers are configured to run via `npx` and will be automatically downloaded when needed. Configuration files:

- `.vscode/mcp.json` - VS Code MCP configuration
- `mcp-config.json` - Project-level MCP configuration

### 2. Agent Workflow

The project uses 9 specialized agents located in `.github/agents/`:

1. **Requirements Agent** - Converts requests into user stories and acceptance criteria
2. **Design Agent** - Creates architectural blueprints using AWS best practices
3. **Implementation Agent** - Writes production code
4. **Testing Agent** - Generates automated tests
5. **Code Scan Agent** - Performs security vulnerability scanning
6. **Code Review Agent** - Reviews code for compliance
7. **Infra Agent** - Generates AWS CloudFormation templates
8. **Deployment Agent** - Deploys using AWS CDK/CLI
9. **Monitoring Agent** - Monitors application health via CloudWatch

### 3. Document-Driven Development

- `Requirements.md` - Source of truth for user stories
- `Architecture.md` - Architectural blueprint

## Usage

Each agent loads only the MCP servers it needs:

```
Requirements → aws-kb
Design → aws-kb, aws-doc, aws-diagram
Implementation → aws-kb
Testing → (no MCP servers)
Code Scan → security-scan
Code Review → aws-kb
Infra → aws-cloudformation
Deployment → aws-cdk-cli
Monitoring → aws-cloudwatch, aws-app-signals
```

## Requirements

- Node.js (for npx to run MCP servers)
- AWS CLI configured (for AWS MCP servers)
- VS Code or compatible IDE with MCP support

## Getting Started

1. Clone this repository
2. Ensure Node.js is installed
3. The MCP servers will be automatically loaded when agents need them
4. Start with the Requirements Agent to begin your development workflow

## More Information

See `.github/copilot-instructions.md` for detailed AI agent guidance.
