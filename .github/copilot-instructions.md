# SampleApp - AI Coding Agent Instructions

## Project Overview

This is an **agent-orchestrated AWS development workspace** that uses specialized AI agents to manage the complete software development lifecycle - from requirements gathering through deployment and monitoring. The project is configured to work with AWS cloud services and follows a structured, multi-agent workflow.

## Architecture: Multi-Agent Development Pipeline

The project implements a **9-agent handoff workflow** located in `.github/chatmodes/*.agent.md`:

```
Requirements → Design → Implementation → Testing → Code Scan → Code Review → Infrastructure → Deployment → Monitoring
     ↑                                                                                                          |
     └──────────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### Agent Workflow Chain

1. **Requirements Agent** (`requirements.agent.md`) - Converts user requests into formal user stories and acceptance criteria, outputs `Requirements.md`
2. **Design Agent** (`design.agent.md`) - Creates architectural blueprints in `Architecture.md` using AWS best practices
3. **Implementation Agent** (`implementation.agent.md`) - Writes production code adhering to Architecture.md specifications
4. **Testing Agent** (`testing.agent.md`) - Generates automated unit and integration tests validating acceptance criteria
5. **Code Scan Agent** (`codescan.agent.md`) - Performs static analysis for security vulnerabilities and code quality
6. **Code Review Agent** (`codereview.agent.md`) - Reviews code for compliance with AWS standards and coding principles
7. **Infra Agent** (`infra.agent.md`) - Generates AWS CloudFormation IaC templates (YAML/JSON)
8. **Deployment Agent** (`deployment.agent.md`) - Deploys code using AWS CDK/CLI
9. **Monitoring Agent** (`monitoring.agent.md`) - Observes application health via CloudWatch and feeds back to Requirements

## Key Conventions

### Agent Tool Patterns

- **AWS Knowledge Base Tools**: All agents reference `aws-kb/*` for architectural and compliance standards
- **AWS Service Tools**: Agents use specialized toolsets:
  - Design: `aws-doc/*`, `aws-diagram/*` for architecture visualization
  - Infra: `aws-cloudformation/*` for IaC generation
  - Deployment: `aws-cdk-cli/*` for deployment execution
  - Monitoring: `aws-cloudwatch/*`, `aws-app-signals/*` for observability
  - Code Scan: `security-scan/*` for OWASP Top 10 vulnerability detection

### Document-Driven Development

- **Requirements.md**: Source of truth for user stories and acceptance criteria
- **Architecture.md**: Detailed architectural blueprint focusing on security, scalability, and cost-efficiency
- All agents must reference these documents to maintain alignment throughout the pipeline

### Handoff Protocol

- Agents use explicit `handoffs` with `send: true/false` to control automatic transitions
- Manual approval gates exist at critical points (Requirements → Design, Design → Implementation)
- Continuous feedback loop from Monitoring back to Requirements for iterative improvement

## Development Workflow

### Starting New Features

1. Begin with **Requirements Agent** - never skip requirements gathering
2. Wait for user approval of `Requirements.md` before proceeding
3. Follow the handoff chain sequentially - each agent builds on the previous agent's output

### Code Quality Gates

- **Testing Agent** ensures high code coverage before security scanning
- **Code Scan Agent** identifies vulnerabilities before code review
- **Code Review Agent** must approve before infrastructure generation
- Do not modify code in scan/review phases - only generate reports and recommendations

### Infrastructure as Code

- Infrastructure is **generated but not deployed** by the Infra Agent
- CloudFormation templates must match security and naming conventions from `Architecture.md`
- Deployment Agent handles actual provisioning after manual review

## Integration Points

### SpecStory Extension Integration

- `.specstory/` directory maintains AI chat history and project identity
- `.specstory/history/` contains auto-saved markdown sessions for context continuity
- `.specstory/.project.json` provides persistent workspace identity (workspace_id: `b421-8a6a-81bf-1caa`)
- Reference previous sessions via `@` mentions for maintaining context across chat sessions

### External Dependencies

- **AWS Services**: Primary cloud platform - all architecture decisions must consider AWS-native solutions
- **CloudFormation/CDK**: Standard IaC approach - prefer CloudFormation templates over manual console work
- **CloudWatch/App Signals**: Standard observability stack - all deployments must include monitoring configuration

## Agent-Specific Guidelines

### When Acting as Implementation Agent
- Always consult `Architecture.md` before writing any code
- Use `aws-kb/*` tools to verify AWS service integration patterns
- Create files directly with the `edit` tool - no manual file creation steps
- Ensure Requirements.md acceptance criteria are fully addressed

### When Acting as Testing Agent
- Generate tests for files created/modified by Implementation Agent
- Test coverage must validate all acceptance criteria from Requirements.md
- Provide summary of test results including coverage metrics

### When Acting as Code Review Agent
- Review against three criteria: coding principles, AWS standards (`aws-kb/*`), and Code Scan results
- Either propose specific actionable changes OR approve for deployment
- Never approve code with critical security findings from Code Scan

### When Acting as Monitoring Agent
- Generate concise feedback reports with specific recommendations
- Identify performance bottlenecks and resource waste patterns
- Feedback should reference specific Architecture.md components when suggesting improvements

## Project-Specific Patterns

### No Source Code Yet
This workspace is **infrastructure-only** at present - no application source code exists. When implementing:
- Create appropriate directory structure based on Architecture.md
- Follow AWS service-specific patterns from `aws-kb/*`
- Maintain separation between application code and infrastructure code

### Chat Modes
The `.github/chatmodes/` directory contains agent definitions for specialized workflows. Reference these for understanding agent capabilities and handoff patterns.

## Common Pitfalls to Avoid

- ❌ Skipping the Requirements Agent - always start with formal requirements
- ❌ Deploying infrastructure without Code Review approval
- ❌ Modifying code during scan/review phases (agents should only report)
- ❌ Ignoring handoff chain - each agent builds on previous outputs
- ❌ Creating architecture without consulting AWS knowledge base tools

## Quick Reference

- **Start here**: Requirements Agent → create Requirements.md
- **Design phase**: Consult `aws-kb/*`, `aws-doc/*`, `aws-diagram/*`
- **Implementation**: Follow Architecture.md strictly, use `edit` tool
- **Quality assurance**: Test → Scan → Review (in that order)
- **Deployment**: Infra generates templates → Deployment executes → Monitoring observes
