# Design - [Project Name]

**Pattern**: Modern Development Workflow

**Design Philosophy**: Foundation → Automation → Deployment → Observability

---

## Architecture Overview

**Application Architecture**: [Microservices, Monolith, Serverless, etc.]

**Deployment Target**: [Kubernetes, Cloud Functions, VMs, etc.]

**Automation Strategy**: [CI/CD tool, GitOps approach]

---

## Phase 1 Design: Foundation

**Core Functionality**:
- [Component 1]: [Description]
- [Component 2]: [Description]
- [Component 3]: [Description]

**API Design**:
- Endpoints: [List key endpoints]
- Authentication: [Strategy]
- Versioning: [Approach]

**Data Layer**:
- Storage: [Database, object storage, etc.]
- Schema: [Design approach]
- Migrations: [Strategy]

---

## Phase 2 Design: Automation

**CI/CD Pipeline**:
```
Code Push
  ↓
Lint & Format Check
  ↓
Unit Tests
  ↓
Build (Docker image)
  ↓
Integration Tests
  ↓
Security Scan
  ↓
Deploy to Staging
  ↓
E2E Tests
  ↓
Manual Approval
  ↓
Deploy to Production
```

**Testing Strategy**:
- Unit: [Framework, coverage target]
- Integration: [Approach]
- E2E: [Tool, critical paths]
- Performance: [Benchmarks]

**Quality Gates**:
- Code coverage: [Threshold]
- Linting: [Standards]
- Security: [Scan tools]
- Performance: [Criteria]

---

## Phase 3 Design: Deployment

**Containerization**:
```dockerfile
# Multi-stage build example
FROM builder AS build
# Build steps

FROM runtime
# Minimal runtime
```

**Infrastructure as Code**:
- Tool: [Terraform, CloudFormation, Pulumi]
- Modules: [Reusable components]
- State management: [Backend config]

**Orchestration** (if applicable):
- Platform: [Kubernetes, ECS, etc.]
- Deployment strategy: [Rolling, blue-green, canary]
- Resource limits: [CPU, memory]
- Autoscaling: [HPA config]

**Environment Strategy**:
- Development: [Config]
- Staging: [Config]
- Production: [Config]
- Parity: [How to maintain]

---

## Phase 4 Design: Observability

**Logging**:
- Format: [Structured JSON]
- Correlation: [Trace IDs]
- Aggregation: [ELK, Loki, CloudWatch]
- Retention: [Policy]

**Metrics**:
- Exposition: [Prometheus /metrics endpoint]
- Key metrics: [RED: Rate, Errors, Duration]
- Custom metrics: [Business KPIs]
- Dashboards: [Grafana, CloudWatch]

**Tracing**:
- Implementation: [OpenTelemetry]
- Sampling: [Strategy]
- Backend: [Jaeger, Zipkin, Tempo]

**Alerting**:
- Alert manager: [Tool]
- Alert rules: [Conditions]
- Notification channels: [Slack, PagerDuty, email]
- On-call: [Rotation, escalation]

**Health Checks**:
- `/health`: Liveness (is app running?)
- `/ready`: Readiness (can app serve traffic?)
- `/metrics`: Prometheus metrics

---

## Security Design

**Authentication & Authorization**:
- Mechanism: [JWT, OAuth, etc.]
- RBAC/ABAC: [Approach]

**Secrets Management**:
- Storage: [Vault, Secrets Manager, etc.]
- Rotation: [Strategy]
- Access: [Principle of least privilege]

**Vulnerability Management**:
- Image scanning: [Trivy, Snyk, etc.]
- Dependency scanning: [Dependabot, etc.]
- Runtime security: [Falco, etc.]

**Network Security**:
- Encryption: [TLS everywhere]
- Network policies: [K8s network policies, etc.]
- Firewall rules: [Design]

---

## GitOps Design

**Git Structure**:
```
repo/
├── src/           # Application code
├── infra/         # Infrastructure as code
├── k8s/           # Kubernetes manifests
├── .github/       # CI/CD workflows
└── docs/          # Documentation
```

**Branching Strategy**: [Trunk-based, GitFlow, etc.]

**Deployment Flow**:
1. Merge to main
2. CI builds and tests
3. CD deploys to staging
4. Manual approval
5. CD deploys to production
6. GitOps reconciles state

---

## Disaster Recovery

**Backup Strategy**:
- Data: [What, frequency, retention]
- Config: [Version controlled]
- Secrets: [Backup approach]

**Rollback Procedures**:
- Application: [Via Git revert, image tag]
- Infrastructure: [Terraform/IaC rollback]
- Database: [Backup restore, migration rollback]

**RTO/RPO**:
- Recovery Time Objective: [Target]
- Recovery Point Objective: [Target]

---

## Cross-Domain Examples

**Microservice**: REST API → Docker → GitHub Actions → K8s → Prometheus/Grafana

**Doc-as-Code**: Markdown → Git → MkDocs build → GitHub Pages → Google Analytics

**Workflow Automation**: YAML workflow → Git → Workflow engine → Execute → Audit logs

**GitOps Infra**: Terraform → Git → Atlantis → Apply → Terraform Cloud monitoring

**Design System**: React components → npm package → Storybook → NPM registry → Usage analytics

---

**Generated from Ouroboros Pattern**: Modern Development Workflow
**Template Version**: 1.0
**Last Updated**: 2025-10-25
