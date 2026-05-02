# Standards & API Reference

> Project: Infrastructure Cost Optimizer · Generated: 2026-05-03

## Industry Standards & Specifications

### FinOps Framework & Specifications

**FinOps Foundation Framework**
- **Official URL:** https://www.finops.org/framework/
- **Description:** The primary industry-led operating model and cultural practice for cloud financial management. Defines three operational phases (Inform, Optimize, Operate), six core capabilities, and maturity levels. Maintained under the Linux Foundation with FinOps Certified Practitioner (FCP) and tools certifications.
- **Relevance:** Foundational standard that Infrastructure Cost Optimizer must align with. Provides vocabulary, maturity models, and buyer personas (FinOps Practitioners, Engineering/SRE Leads, FP&A teams).

**FOCUS™ v1.2 — FinOps Open Cost & Usage Specification**
- **Official URL:** https://focus.finops.org/
- **Specification:** https://focus.finops.org/focus-specification/
- **GitHub Repository:** https://github.com/FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec
- **Description:** Vendor-neutral specification for normalizing cloud billing data across AWS, Azure, GCP, Kubernetes, SaaS, and data center vendors. Version 1.2 ratified May 29, 2025. Defines consistent column schemas, metrics, and chargeback/allocation methodologies to reduce cross-vendor data wrangling.
- **Relevance:** Core standard for cost data ingestion and normalization. Infrastructure Cost Optimizer should natively ingest and export FOCUS-compliant data, enabling seamless integration with the FinOps ecosystem.

**OpenCost Specification v1.3 — CNCF Incubating Project**
- **Official URL:** https://opencost.io/docs/specification/
- **GitHub:** https://github.com/opencost/opencost
- **CNCF Project:** https://www.cncf.io/
- **Description:** Open standard for measuring and allocating Kubernetes infrastructure costs to workloads, namespaces, labels, and deployments. Supports AWS, Azure, GCP, and on-prem environments. Exports cost metrics in Prometheus format for observability integration.
- **Relevance:** Mandatory standard for Kubernetes cost allocation component. Infrastructure Cost Optimizer should implement OpenCost Specification v1.3 natively and remain compatible with existing OpenCost deployments.

### API & Data Standards

**OpenAPI Specification (OAS) v3.2**
- **Official URL:** https://spec.openapis.org/oas/v3.2.0.html
- **Initiative:** https://www.openapis.org/
- **Description:** Standard, language-agnostic format for describing RESTful APIs in YAML or JSON. Defines endpoints, request/response schemas, authentication, and rate limits. Enables automatic code generation, interactive documentation (Swagger UI), and contract testing.
- **Relevance:** Industry-standard API documentation format. All REST API endpoints (billing, cost allocation, anomaly detection, recommendations) should be documented with OpenAPI v3.2 specifications.

**GraphQL Specification (October 2021)**
- **Official URL:** https://spec.graphql.org/October2021/
- **GitHub:** https://github.com/graphql/graphql-spec
- **Description:** Open-source query language for APIs with strongly-typed schema, introspection, and client-controlled field-level granularity. Enables flexible data fetching for cost queries and complex filtering across dimensions.
- **Relevance:** Optional complementary API layer for cost data queries. Consider GraphQL endpoint for Vantage Query Language (VQL)-like filtering of cost data across dimensions (teams, services, time ranges, tags).

**JSON Schema Standard**
- **Official URL:** https://json-schema.org/specification
- **Description:** Declarative standard for defining, validating, and documenting JSON data structure, types, and constraints. Enables schema-driven validation in APIs, configuration files, and data interchange.
- **Relevance:** Use JSON Schema for validating cost data payloads, cost allocation rules, and API request/response validation. Integrate schema validation into CI/CD pipelines to ensure data integrity.

### Cloud Architecture & Well-Being Frameworks

**AWS Well-Architected Framework — Cost Optimization Pillar**
- **Official URL:** https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/
- **Description:** AWS design principles and best practices for cost-optimized workloads: appropriate resource selection, matching supply to demand, spending awareness, and avoiding unnecessary costs. References AWS Cost Explorer, Budgets, and Trusted Advisor.
- **Relevance:** Standard reference for AWS rightsizing, commitment optimization, and waste elimination strategies.

**Google Cloud Well-Architected Framework — Cost Optimization**
- **Official URL:** https://cloud.google.com/architecture/framework/cost-optimization
- **Description:** GCP-specific guidance on aligning cloud spending with business value, fostering cost awareness culture, and continuous optimization via GKE Autopilot, Cloud Run, and workload-appropriate autoscaling.
- **Relevance:** Standard reference for GCP cost optimization strategies and architecture patterns.

**Azure Well-Architected Framework — Cost Optimization**
- **Official URL:** https://learn.microsoft.com/en-us/azure/well-architected/cost-optimization/
- **Description:** Microsoft's guidance on budget management, Reserved Instance analysis, cost governance, and integration with Azure Advisor for continuous optimization.
- **Relevance:** Standard reference for Azure cost optimization strategies and governance patterns.

### Security & Authentication Standards

**OAuth 2.0 Framework (RFC 6749, RFC 6750)**
- **Official URL:** https://tools.ietf.org/html/rfc6749
- **Description:** IETF-standardized authorization framework enabling secure delegation of access to protected resources. Defines authorization code, client credentials, refresh tokens, and scoped access flows.
- **Relevance:** Standard for API authentication and third-party integrations. Infrastructure Cost Optimizer should support OAuth 2.0 for cloud provider authentication (AWS, Azure, GCP), webhook integrations, and user access control.

**OpenID Connect (OIDC) 1.0**
- **Official URL:** https://openid.net/developers/how-connect-works/
- **Description:** Authentication layer built on OAuth 2.0 enabling user identity verification, Single Sign-On (SSO), and interoperable user profile information exchange. Certified implementations by Microsoft, Google, Okta, and others.
- **Relevance:** Standard for user authentication in dashboard and CLI. Enable OIDC integration for enterprise SSO (Okta, Azure AD, Google Workspace).

### ISO & General Compliance Standards

**ISO/IEC 27001 — Information Security Management**
- **Official URL:** https://www.iso.org/standard/27001
- **Description:** International standard for establishing and maintaining information security management systems (ISMS). Requires confidentiality, integrity, and availability controls for sensitive data.
- **Relevance:** Foundational security standard for cost data (which often contains sensitive business information). Implement encryption in transit (TLS), at rest, and access control; conduct regular audits.

**ISO/IEC 27701 — Privacy Extension**
- **Official URL:** https://www.iso.org/standard/27701
- **Description:** Extension to ISO 27001 addressing personal data protection and privacy requirements, including GDPR and CCPA compliance. Defines privacy controls, data subject rights, and processor obligations.
- **Relevance:** Relevant if cost data includes PII (personally identifiable information in tags, resource names, or allocation mappings). Ensure data retention policies and user consent mechanisms.

**ISO/IEC 19944:2017 — Cloud Computing Data Management**
- **Official URL:** https://www.iso.org/standard/66674.html
- **Description:** Standard defining data flow, data categories, and data use models in cloud computing ecosystems. Provides taxonomy for understanding data lifecycle and governance.
- **Relevance:** Informs cost data governance: understand which data categories cost data belongs to, data residency requirements, and retention policies.

### Observability & Metrics Standards

**Prometheus Exposition Format & OpenMetrics**
- **Official URL:** https://prometheus.io/docs/instrumenting/exposition_formats/
- **OpenMetrics Spec:** https://openmetrics.io/
- **Description:** De-facto standard for exposing infrastructure and application metrics in time-series format. OpenCost, Kubernetes metrics exporters, and most observability tools export data in this format.
- **Relevance:** Infrastructure Cost Optimizer should export cost metrics in Prometheus format to enable integration with Grafana, Thanos, and existing observability stacks. Use standard metric naming (`cost_*`, `allocation_*`).

## Similar Products — Developer Documentation & APIs

### CloudZero — Cloud Cost Intelligence Platform

- **Product Description:** Enterprise FinOps platform specializing in 100% cost allocation and unit economics (cost per customer, per feature). Reports 22% average savings in year one with ROI within 3 months. Subscription-based with dedicated FinOps account manager support.
- **Official Website:** https://www.cloudzero.com/
- **API Documentation:** https://docs.cloudzero.com/docs/cloudzero
- **Key API Endpoints:**
  - **Telemetry APIs:** https://docs.cloudzero.com/reference/telemetry-api-1
  - **Billing Costs API:** https://docs.cloudzero.com/reference/getbillingcosts
  - **Unit Cost Metrics:** `POST /unit-cost/v1/telemetry/metric/{metric_name}/sum`
- **SDKs/Libraries:** CloudZero provides REST API; no official SDKs published in major repos (Python, Node, Go).
- **Standards Compliance:** REST API, JSON payloads. Custom Allocation Dimensions DSL with rules-based and telemetry-based split methods.
- **Authentication:** API Key-based authentication
- **Rate Limits:** 60 requests/day for billing costs API; 30-second timeout

### Vantage — Cloud Cost Intelligence Platform

- **Product Description:** Multi-cloud cost transparency platform with AI-powered anomaly detection, forecasting, cost allocation, and AI chat interface. Supports AWS, Azure, GCP, Snowflake, Datadog, MongoDB Atlas. Monthly SaaS subscription tiered by cloud spend tracked (no per-seat fees).
- **Official Website:** https://www.vantage.sh/
- **API Documentation:** https://docs.vantage.sh/api
- **ReadMe Documentation:** https://vantage.readme.io/
- **Key Features:**
  - **Vantage Query Language (VQL):** SQL-like language for filtering cost data with normalized schema across providers
  - **Resource Costs API:** Retrieve resource-level costs for 100+ supported resources across 8 providers
  - **Forecasted Costs API:** `GET /cost_reports/{cost_report_token}/forecasted_costs`
- **SDKs/Libraries:** Python SDK available at https://github.com/vantage-sh/vantage-python (auto-generated from OpenAPI spec)
- **Standards Compliance:** REST API with OpenAPI 2.0 and OpenAPI 3.0.1 specifications; supports custom Swagger UI and Postman integrations
- **Authentication:** API Key (Bearer token)

### Harness Cloud Cost Management (CCM)

- **Product Description:** Multi-cloud FinOps platform with AutoStopping (shuts idle resources), Commitment Orchestrator (RI/Savings Plan automation), and governance rules. FinOps Foundation certified. Claims up to 70% savings through automation.
- **Official Website:** https://www.harness.io/products/cloud-cost-management
- **API Documentation:** https://developer.harness.io/docs/cloud-cost-management/
- **Key API Endpoints:**
  - **Recommendations Overview:** `GET /ccm/api/recommendation/overview/list` (includes tags field, new in latest version)
  - **Anomaly Fetch API:** Enhanced perspective query filters supporting AWS Account Name/ID, Service, and Usage Type
- **Developer Hub:** https://developer.harness.io/docs/cloud-cost-management/
- **Release Notes:** https://developer.harness.io/release-notes/cloud-cost-management/
- **Standards Compliance:** REST API with JSON payloads; custom filtering and perspective management
- **Authentication:** Bearer token (API key)

### Finout — Enterprise FinOps Platform

- **Product Description:** Enterprise platform emphasizing 100% cost allocation without requiring complete tagging. Covers AWS, GCP, Azure, Kubernetes, and SaaS spend in unified view. Features FairShare Cost allocation, Virtual Tagging, and Shared Cost Reallocation. Claims 30% cost reduction within one year.
- **Official Website:** https://www.finout.io/
- **API Documentation:** https://docs.finout.io/api/finout-api
- **Key API Endpoints:**
  - **Cost API:** https://docs.finout.io/api/finout-api/cost-api (query costs using Finout Views with 90-day lookback)
  - **Cost and Usage Types:** https://docs.finout.io/get-started-with-finout/cost-and-usage-types
  - **Kubernetes Cost Calculation:** https://docs.finout.io/integrations/kubernetes-prometheus/kubernetes-how-finout-calculates-k8s-costs
  - **Telemetry Integration:** https://docs.finout.io/integrations/telemetry
- **Standards Compliance:** REST API; supports FOCUS-aligned cost schema; integrates with Prometheus for Kubernetes metrics
- **Authentication:** API Key-based
- **Allocation Methods:** FairShare Cost, Virtual Tagging, Shared Cost Reallocation, Telemetry-based allocation

### Infracost — Terraform Cost Estimation

- **Product Description:** Open-source "Shift FinOps Left" tool showing cost estimates for Terraform changes directly in pull requests. Supports 1,100+ Terraform resources across AWS, Azure, GCP. Core CLI is open source (Apache 2.0); Infracost Cloud adds team dashboards and governance.
- **Official Website:** https://www.infracost.io/
- **GitHub Repository:** https://github.com/infracost/infracost
- **Documentation:** https://www.infracost.io/docs/
- **Key Features:**
  - Real-time Terraform plan cost estimation
  - CI/CD integration (GitHub Actions, GitLab CI, Azure Pipelines, etc.)
  - Pull request comment integration with cost impact analysis
  - Policy-as-code governance rules
- **SDKs/Libraries:** Official CLI (Go); community SDKs in Python, Node.js, and Ruby
- **Standards Compliance:** Terraform HCL parsing; JSON output format compatible with custom integrations
- **Authentication:** API Key required for live pricing data fetching
- **Unique Value:** Only open-source tool integrating cost estimation directly into IaC workflow before deployment

### CAST AI — Kubernetes Optimization Platform

- **Product Description:** All-in-one Kubernetes automation platform for cost optimization, security, and reliability across AWS, Azure, GCP, and on-prem. Features Workload Autoscaler (in-place pod rightsizing, Live Migration), predictive spot interruption detection (30-minute advance notice), and resource optimization. Claims up to 60% cost reduction.
- **Official Website:** https://cast.ai/
- **Documentation:** https://docs.cast.ai/docs/
- **Getting Started:** https://docs.cast.ai/docs/getting-started
- **Key API Resources:**
  - **Workload Optimization Overview:** https://docs.cast.ai/docs/workload-autoscaling-overview
  - **In-Place Pod Resizing:** https://docs.cast.ai/docs/woop-in-place-resizing
  - **GitHub Agent:** https://github.com/castai/k8s-agent
- **Integration Methods:** Kubernetes Custom Resource Definitions (CRDs), API-driven recommendations
- **Standards Compliance:** Kubernetes-native APIs; supports kubectl, Helm, and custom operators
- **Authentication:** Token-based API authentication
- **Unique Value:** Predictive spot interruption detection and zero-downtime workload migration; integration with existing Kubernetes autoscaling ecosystem

### nOps — AWS Cost Optimization Platform

- **Product Description:** AWS-focused continuous RI/Savings Plan management and compute rightsizing. Integrates with Karpenter for Kubernetes node optimization. Spend-based subscription starting around $1,000/month for smaller environments. Available on AWS Marketplace.
- **Official Website:** https://www.nops.io/
- **API Documentation:** https://help.nops.io/docs/nops/developer-intro/
- **Help Center:** https://help.nops.io/
- **Integrations Overview:** https://help.nops.io/docs/agents-integrations/integrations/
- **Key Capabilities:**
  - Real-time AWS cost and usage monitoring via API
  - Custom reporting and analytics integration
  - Cost alerts and anomaly detection
  - Karpenter integration for Kubernetes node optimization
- **Standards Compliance:** REST API; AWS CloudWatch integration; Terraform modules for deployment
- **Authentication:** API Key-based
- **Unique Value:** Karpenter integration for managed Kubernetes node optimization on AWS

### Cloud Custodian — Open-Source Governance Engine

- **Product Description:** CNCF Incubating Project providing vendor-neutral rules engine for cloud governance, security, and cost optimization. Policies written in simple YAML DSL enabling resource filtering and automated actions across AWS, Azure, GCP, Kubernetes, and OpenStack.
- **Official Website:** https://cloudcustodian.io/
- **GitHub Repository:** https://github.com/cloud-custodian/cloud-custodian
- **Documentation:** https://cloudcustodian.io/docs/
- **Key Features:**
  - YAML-based policy DSL (simple, composable filters and actions)
  - Multi-cloud support (AWS, Azure, GCP, Kubernetes, OpenStack)
  - Cost optimization policies (garbage collection of unused resources, off-hours resource management)
  - Real-time compliance enforcement
- **Use Cases:** Tag policy enforcement, instance lifecycle management, cost governance
- **Standards Compliance:** YAML configuration; integrates with native cloud APIs; supports webhooks and custom actions
- **Authentication:** Cloud provider credentials (AWS IAM, Azure AD, GCP Service Accounts)
- **Unique Value:** Simple YAML DSL reduces barrier to policy authoring vs. complex rule engines; open-source, independent of vendor

### OpenCost — Open-Source Kubernetes Cost Monitoring

- **Product Description:** CNCF Incubating Project (as of October 2024) providing vendor-neutral real-time Kubernetes cost monitoring. Implements OpenCost Specification v1.3; exports to Prometheus. Supports GCP, AWS, Azure, on-prem. Free to deploy on any Kubernetes 1.8+ cluster.
- **Official Website:** https://opencost.io/
- **Documentation:** https://opencost.io/docs/
- **Specification:** https://opencost.io/docs/specification/
- **GitHub Repository:** https://github.com/opencost/opencost
- **CNCF Project:** https://www.cncf.io/projects/opencost/
- **Key Features:**
  - Real-time cluster cost allocation by namespace, pod, label, deployment
  - Multi-cloud cost data aggregation (AWS, Azure, GCP)
  - Prometheus metrics export for integration with Grafana
  - Idle cost calculation and resource efficiency metrics
- **Deployment:** Docker, Kubernetes Helm chart, standalone binary
- **Standards Compliance:** Implements OpenCost Specification v1.3; exports Prometheus format; YAML configuration
- **Integration:** Works with existing Prometheus/Grafana stacks; compatible with Kubecost
- **Unique Value:** CNCF incubating project ensures vendor-neutral governance; native Kubernetes integration; Prometheus-native metrics export

## Notes

### Gaps in Current Standards

1. **No ISO standard for cloud cost management specifically.** FinOps Framework and FOCUS specification are authoritative industry references rather than international ISO standards. This represents an opportunity for Infrastructure Cost Optimizer to become a de-facto standard implementation.

2. **Multi-cloud cost allocation remains inconsistent.** While FOCUS v1.2 standardizes billing data schemas, allocation methodologies across AWS (cost allocation tags), Azure (resource groups/subscriptions), and GCP (label hierarchies) remain vendor-specific. Infrastructure Cost Optimizer should provide unified allocation semantics.

3. **AI/ML workload cost attribution is nascent.** No formal standard yet exists for GPU-level cost allocation, token-level LLM API cost tracking, or training-vs-inference separation. This is a greenfield opportunity for Industry Cost Optimizer.

4. **Developer-facing cost feedback standards are underdeveloped.** OpenCost and FOCUS focus on operational dashboards and chargeback reporting; standards for embedding cost feedback into pull requests, deployment pipelines, and CI/CD tools are still emerging. Infracost addresses IaC estimation but not runtime costs.

### Emerging Standards & Watch List

- **CNCF Container Cost Attribution:** As of May 2026, discussions within CNCF SIG-Observability are exploring finer-grained cost attribution models for container registries, image sizes, and layer-level cost allocation.
- **FOCUS v2.0 Planning:** FinOps Foundation is discussing v2.0 enhancements to FOCUS for real-time billing API schemas, event-driven cost reporting, and GraphQL query interfaces.
- **Model Context Protocol (MCP) for FinOps:** Emerging pattern of exposing cost data and recommendations via MCP servers, enabling AI agents and Claude to query cost and provide recommendations without custom integrations.

### Recommended Implementation Priorities

1. **FOCUS v1.2 native ingestion and export** — Ensure all cost data pipelines ingest/export FOCUS-compliant schemas for ecosystem compatibility
2. **OpenCost Specification v1.3 compliance** — Native Kubernetes cost allocation must implement the spec exactly for drop-in replacement with existing OpenCost deployments
3. **OpenAPI v3.2 documentation** — All REST API endpoints must be documented with complete OpenAPI specs for SDKs and integrations
4. **OAuth 2.0 + OIDC authentication** — Standard for cloud provider and user authentication; enable enterprise SSO integrations
5. **Prometheus metrics export** — Export cost and anomaly metrics in Prometheus format for observability stack integration
6. **YAML policy-as-code (Cloud Custodian alignment)** — Policy engine output must be compatible with Cloud Custodian for governance enforcement
