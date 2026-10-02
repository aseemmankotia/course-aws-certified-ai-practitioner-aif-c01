# Domain 5: Security, Compliance & Governance Cheat Sheet

## IAM Permissions for Bedrock (Heavily Tested)

| Permission | Purpose | Resource ARN Format |
|------------|---------|--------------------|
| `bedrock:InvokeModel` | Invoke foundation model | `arn:aws:bedrock:region::foundation-model/model-id` |
| `bedrock:ListFoundationModels` | List available models | `*` (no resource restriction) |
| `bedrock:GetFoundationModel` | Get model details | `arn:aws:bedrock:region::foundation-model/model-id` |

**Exam Rule:** Always restrict `bedrock:InvokeModel` to specific model ARNs for least privilege.

## Encryption (Heavily Tested)

### Data at Rest
| Service | Encryption Method | Cost | Exam Notes |
|---------|------------------|------|------------|
| S3 | KMS CMK (SSE-KMS) | $1/month per key + $0.03/10k requests | Customer-managed keys for compliance |
| SageMaker Notebooks | EBS volume encryption with KMS | $1/month per key | Must enable at creation |
| SageMaker Training | EBS volumes with KMS | $1/month per key | Encrypts training artifacts |

### Data in Transit
- **TLS 1.2+** automatically enforced for all Bedrock and SageMaker API calls
- **No configuration needed** — exam trick: if question asks how to encrypt in transit, answer is "already encrypted"

## VPC Endpoints for Private Access (Heavily Tested)

```
Service Endpoint Name: com.amazonaws.region.bedrock-runtime
Use Case: No internet access requirement
Cost: $0.01/hour per AZ + $0.01/GB data processed
```

**Exam Scenario:** "Ensure Bedrock calls never traverse public internet" → Create VPC endpoint with PrivateLink

## Logging & Auditing

### CloudTrail for API Logging
- **Enable data events** to log `bedrock:InvokeModel` calls
- **Cost:** $0.025/GB/month (S3 Standard storage)
- **Lifecycle:** Move to Glacier Deep Archive ($0.00099/GB/month) for long-term retention
- **Logs Include:** Model ID, request parameters, caller identity, timestamp

### Amazon Macie for PII Discovery
- **Cost:** $1/GB scanned
- **Use Case:** ML-powered scan of S3 for PII, sensitive data
- **Continuous Monitoring:** Automated sensitive data discovery
- **Exam Trigger Words:** "find PII", "scan for sensitive data", "detect personal information"

## Compliance Automation

### AWS Audit Manager
- **Pre-built frameworks:** SOC 2, PCI-DSS, HIPAA, GDPR, ISO 27001
- **Automated evidence collection** from CloudTrail, Config, Security Hub
- **Output:** Audit-ready compliance reports
- **Exam Trigger:** "demonstrate compliance", "audit preparation", "SOC 2 evidence"

### AWS Config
- **Continuous compliance assessment** of resource configurations
- **Use Case:** Ongoing monitoring, not audit report generation
- **Exam Distinction:** Config = continuous monitoring | Audit Manager = audit preparation

## Service Comparisons (Common Exam Traps)

| Requirement | Correct Service | Wrong Choices (Exam Distractors) |
|-------------|----------------|----------------------------------|
| Find PII in S3 | Macie ($1/GB) | GuardDuty (threat detection), Inspector (vulnerabilities) |
| Log Bedrock API calls | CloudTrail data events | VPC Flow Logs (network), CloudWatch (metrics) |
| Private Bedrock access | VPC endpoint (com.amazonaws.region.bedrock-runtime) | NAT Gateway (still internet), Direct Connect (overkill) |
| SOC 2 compliance | Audit Manager | Security Hub (findings), Config (continuous) |
| Encrypt training data at rest | KMS CMK for S3/EBS | TLS (in transit), network isolation (different purpose) |

## Shared Responsibility Model (Always Tested)

### AWS Responsibilities
- Infrastructure security (physical, hypervisor)
- Bedrock model availability and patching
- API endpoint DDoS protection
- Data center security

### Customer Responsibilities (Exam Focus)
- **IAM policies** for bedrock:InvokeModel, least privilege
- **Data encryption:** KMS keys, S3 bucket policies
- **VPC configuration:** Endpoints, security groups
- **Logging:** Enable CloudTrail data events
- **Access management:** Who can invoke models

**Exam Rule:** When in doubt, IAM and encryption are ALWAYS customer responsibility.

## Key Numbers to Memorize

- KMS CMK: **$1/month** per key
- Macie scanning: **$1/GB** scanned
- CloudTrail S3 storage: **$0.025/GB/month** (Standard)
- Glacier Deep Archive: **$0.00099/GB/month**
- VPC endpoint: **$0.01/hour** per AZ + **$0.01/GB** processed
- TLS version: **1.2+** (automatic)

## Quick Decision Tree

```
Need to control encryption keys? → KMS CMK ($1/month)
Need to find PII in S3? → Macie ($1/GB)
Need private AWS service access? → VPC endpoint (PrivateLink)
Need to log API calls? → CloudTrail data events
Need SOC 2 compliance? → Audit Manager
Need continuous monitoring? → AWS Config
Need least privilege IAM? → Restrict to specific resource ARNs
```
