# MCP Servers Setup

This directory contains configuration for Model Context Protocol (MCP) servers used by the AI agents.

## Configured MCP Servers

### AWS Services
- **aws-kb**: AWS Knowledge Base
- **aws-doc**: AWS Documentation
- **aws-diagram**: AWS Architecture Diagrams
- **aws-cloudformation**: CloudFormation IaC
- **aws-cdk-cli**: AWS CDK CLI
- **aws-cloudwatch**: CloudWatch Monitoring
- **aws-app-signals**: Application Signals

### Security & Quality
- **security-scan**: OWASP Security Scanner

## Configuration Files

- `mcp.json` - VS Code MCP configuration
- `../mcp-config.json` - Project-level configuration

## Notes

**Important**: These MCP server package names are placeholders. AWS MCP servers may need to be:
1. Custom-built for your organization
2. Installed from AWS-specific registries
3. Run as local services

Please verify the actual package names and installation methods for your AWS MCP servers.

## Alternative: Custom MCP Servers

If the AWS MCP servers don't exist as npm packages, you'll need to:

1. Build custom MCP servers following the [MCP specification](https://modelcontextprotocol.io)
2. Update the configuration to point to your local server implementations
3. Configure authentication for AWS services

Example custom server configuration:
```json
{
  "aws-kb": {
    "command": "node",
    "args": ["./servers/aws-kb/index.js"],
    "env": {
      "AWS_REGION": "us-east-1"
    }
  }
}
```
