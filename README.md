# Infrastructure Cost Optimizer

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An open-source, AI-native platform that analyzes cloud spend across AWS, GCP, Azure, and Kubernetes — rightsizing resources, eliminating waste, and surfacing actionable savings opportunities with explainable AI recommendations.

Cloud cost management is a $13.5–15.9B market where 27–29% of spend is wasted every year (Flexera 2025 State of the Cloud Report). Yet the best open-source tools stop at Kubernetes monitoring, every autonomous commitment optimizer is a proprietary black box, and no existing tool provides developers with real-time cost feedback in their normal workflow. This project fills that gap: a self-hosted, fully open platform combining multi-cloud visibility, AI-inferred cost allocation, and developer-facing cost intelligence — the role Prometheus played for observability, applied to FinOps.

---

## Why Infrastructure Cost Optimizer?

- **Commercial consolidation has gutted the open-source ecosystem.** Kubecost is now IBM Apptio. Spot.io and ProsperOps are Flexera. CloudHealth is Broadcom Aria. No independent, production-grade open-source alternative covers multi-cloud rightsizing, commitment management, and cost allocation in a single tool.
- **Native cloud tools are siloed and shallow.** AWS Cost Explorer, Azure Cost Management, and GCP Billing each cover only their own estate and none provide cross-cloud unit economics, anomaly root-cause explanation, or developer-workflow integration.
- **Tagging completeness is the #1 allocation barrier — and it is unsolved in open source.** 100% cost allocation without complete infrastructure tagging is offered by CloudZero and Finout at $20K–$80K/year. No open-source tool applies AI inference to automatically assign untagged resources to owners.
- **AI/ML workload costs are a fast-growing blind spot.** 98% of FinOps teams now manage AI spend (FinOps Foundation 2026), yet no open-source tool provides GPU-level attribution, token-level LLM API cost tracking, or training-vs-inference cost separation.
- **Developers are disconnected from the costs they cause.** The FinOps/engineering disconnect is the primary identified cause of cloud waste, yet cost tools are built for finance dashboards, not pull requests or deployment pipelines.

---

## Key Features

**Multi-Cloud Cost Visibility**
- Ingest billing data from AWS, Azure, and GCP via native billing APIs — no agent deployment required
- Kubernetes cost allocation implementing the OpenCost Specification v1.3, compatible with existing OpenCost deployments
- Multi-cluster aggregated view with bill reconciliation against cloud provider invoices
- SaaS spend ingestion (Datadog, Snowflake, Databricks, OpenAI, Anthropic) for a unified allocation model

**AI-Powered Cost Allocation**
- Automatic tag inference: assigns untagged resources to owners using resource name, VPC membership, IAM policy content, and network topology — no re-tagging campaigns required
- Virtual tags applied at query time without modifying live infrastructure
- Team, product, and business-unit chargeback and showback reporting

**Anomaly Detection and Explanation**
- Anomaly detection with configurable alert thresholds
- LLM-generated root-cause explanations alongside each alert — not just "spend increased 40%" but the probable cause (deployment, traffic event, configuration change)
- Budgeting with forecast-to-budget variance tracking and 12-month forecasting

**Rightsizing and Waste Elimination**
- Compute instance and Kubernetes pod rightsizing recommendations with workload-aware instance family matching
- Idle resource detection and AutoStopping for non-production environments
- Transparent Reserved Instance / Savings Plan recommendation engine with human-readable justifications and confidence scores

**Shift-Left Developer Cost Feedback**
- Pull request cost impact comments for Terraform and CloudFormation before infrastructure is deployed
- Policy-as-code governance with natural language authoring: describe rules in plain English, generate executable YAML
- CLI for local cost exploration and CI/CD pipeline integration

**AI and GPU Workload Attribution**
- GPU utilisation cost allocation at workload level for training and inference jobs
- Token-level LLM API cost tracking across OpenAI, Anthropic, and AWS Bedrock
- Training-vs-inference cost separation for ML platform teams

---

## AI-Native Advantage

Rule-based cost tools detect anomalies but cannot explain them; they generate recommendations but cannot justify them; they identify untagged resources but cannot assign them. This project applies LLMs at three points where rule-based approaches fail: inferring resource ownership from contextual signals that no tag schema can fully capture, generating human-readable root-cause explanations for cost anomalies that currently require manual investigation, and translating governance requirements from natural language into executable policies. The result is a FinOps platform that engineering teams will actually use — because it speaks the language of deployments and pull requests, not just finance dashboards.

---

## Tech Stack & Deployment

Designed for self-hosted deployment as a Helm chart (Kubernetes) or Docker Compose stack, with an optional lightweight CLI for local and CI use. Cost data ingestion is via native cloud billing APIs and the FOCUS™ v1.3 specification (the FinOps Open Cost and Usage Specification), enabling consistent cross-provider normalisation. Kubernetes cost allocation implements the OpenCost Specification v1.3 (CNCF) for compatibility with the existing ecosystem. An MCP server (Model Context Protocol) exposes cost data to AI agents. The policy engine outputs YAML compatible with Cloud Custodian (Apache 2.0) for enforcement.

---

## Market Context

The cloud cost management market is estimated at $13.5–15.9B in 2024–2025, growing at a 17% CAGR toward $78B by 2035 (Market Research Future, Grand View Research). With 27% of cloud spend wasted industry-wide — implying ~$182B in annual waste against a ~$675B global cloud infrastructure market — the addressable savings opportunity dwarfs the tool cost at every pricing tier. Commercial alternatives range from $5K–$30K/year (nOps, CloudCheckr at ~3.5% of cloud spend) to $50K–$200K/year enterprise contracts (Apptio Cloudability, CloudHealth), with mid-market SaaS (CloudZero, Vantage, Finout) at $20K–$80K/year. Primary buyers are FinOps practitioners, engineering and SRE leads, and FP&A teams — all of whom are currently underserved by open-source options.

---

## Project Status

> This project is in the **research and specification phase**.
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
